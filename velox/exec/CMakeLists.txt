# Copyright (c) Facebook, Inc. and its affiliates.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
add_library(
  velox_exec
  Aggregate.cpp
  AggregateFunctionRegistry.cpp
  AggregationMasks.cpp
  AggregateWindow.cpp
  ContainerRowSerde.cpp
  CrossJoinBuild.cpp
  CrossJoinProbe.cpp
  Driver.cpp
  EnforceSingleRow.cpp
  Exchange.cpp
  FilterProject.cpp
  GroupId.cpp
  GroupingSet.cpp
  HashAggregation.cpp
  HashBuild.cpp
  HashJoinBridge.cpp
  HashPartitionFunction.cpp
  HashProbe.cpp
  HashTable.cpp
  JoinBridge.cpp
  Limit.cpp
  LocalPartition.cpp
  LocalPlanner.cpp
  Merge.cpp
  MergeJoin.cpp
  MergeSource.cpp
  Operator.cpp
  OperatorUtils.cpp
  OrderBy.cpp
  PartitionedOutput.cpp
  PartitionedOutputBufferManager.cpp
  PlanNodeStats.cpp
  RowContainer.cpp
  Spill.cpp
  SpillOperatorGroup.cpp
  Spiller.cpp
  StreamingAggregation.cpp
  TableScan.cpp
  TableWriter.cpp
  Task.cpp
  TopN.cpp
  Unnest.cpp
  Values.cpp
  VectorHasher.cpp
  Window.cpp
  WindowFunction.cpp
  WindowPartition.cpp
  AssignUniqueId.cpp)

target_link_libraries(
  velox_exec
  velox_file
  velox_core
  velox_vector
  velox_connector
  velox_time
  velox_codegen
  velox_common_base
  velox_test_util)

if(${VELOX_BUILD_TESTING})
  add_subdirectory(tests)
elseif(${VELOX_BUILD_TEST_UTILS})
  add_subdirectory(tests/utils)
endif()

if(${VELOX_ENABLE_BENCHMARKS})
  add_subdirectory(benchmarks)
endif()
