---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794716"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="0e594-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="0e594-102">ODBC Schema Collections</span></span>

<span data-ttu-id="0e594-103">W tej sekcji omówiono obsługę kolekcji schematów dla sterowników ODBC dla Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0e594-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="0e594-104">Sterownik Microsoft SQL Server ODBC</span><span class="sxs-lookup"><span data-stu-id="0e594-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="0e594-105">Sterownik Microsoft SQL Server ODBC obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="0e594-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="0e594-106">Tabelę</span><span class="sxs-lookup"><span data-stu-id="0e594-106">Tables</span></span>

- <span data-ttu-id="0e594-107">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="0e594-107">Indexes</span></span>

- <span data-ttu-id="0e594-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-108">Columns</span></span>

- <span data-ttu-id="0e594-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-109">Procedures</span></span>

- <span data-ttu-id="0e594-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-110">ProcedureColumns</span></span>

- <span data-ttu-id="0e594-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e594-111">ProcedureParameters</span></span>

- <span data-ttu-id="0e594-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="0e594-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-113">Tables and Views</span></span>

|<span data-ttu-id="0e594-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-114">ColumnName</span></span>|<span data-ttu-id="0e594-115">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-116">TABLE_CAT</span></span>|<span data-ttu-id="0e594-117">String</span><span class="sxs-lookup"><span data-stu-id="0e594-117">String</span></span>|
|<span data-ttu-id="0e594-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-118">TABLE_SCHEM</span></span>|<span data-ttu-id="0e594-119">String</span><span class="sxs-lookup"><span data-stu-id="0e594-119">String</span></span>|
|<span data-ttu-id="0e594-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-120">TABLE_NAME</span></span>|<span data-ttu-id="0e594-121">String</span><span class="sxs-lookup"><span data-stu-id="0e594-121">String</span></span>|
|<span data-ttu-id="0e594-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-122">TABLE_TYPE</span></span>|<span data-ttu-id="0e594-123">String</span><span class="sxs-lookup"><span data-stu-id="0e594-123">String</span></span>|
|<span data-ttu-id="0e594-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-124">REMARKS</span></span>|<span data-ttu-id="0e594-125">String</span><span class="sxs-lookup"><span data-stu-id="0e594-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="0e594-126">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="0e594-126">Indexes</span></span>

|<span data-ttu-id="0e594-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-127">ColumnName</span></span>|<span data-ttu-id="0e594-128">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-129">TABLE_CAT</span></span>|<span data-ttu-id="0e594-130">String</span><span class="sxs-lookup"><span data-stu-id="0e594-130">String</span></span>|
|<span data-ttu-id="0e594-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-131">TABLE_SCHEM</span></span>|<span data-ttu-id="0e594-132">String</span><span class="sxs-lookup"><span data-stu-id="0e594-132">String</span></span>|
|<span data-ttu-id="0e594-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-133">TABLE_NAME</span></span>|<span data-ttu-id="0e594-134">String</span><span class="sxs-lookup"><span data-stu-id="0e594-134">String</span></span>|
|<span data-ttu-id="0e594-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0e594-135">NON_UNIQUE</span></span>|<span data-ttu-id="0e594-136">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-136">Int16</span></span>|
|<span data-ttu-id="0e594-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="0e594-138">String</span><span class="sxs-lookup"><span data-stu-id="0e594-138">String</span></span>|
|<span data-ttu-id="0e594-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-139">INDEX_NAME</span></span>|<span data-ttu-id="0e594-140">String</span><span class="sxs-lookup"><span data-stu-id="0e594-140">String</span></span>|
|<span data-ttu-id="0e594-141">WPROWADŹ</span><span class="sxs-lookup"><span data-stu-id="0e594-141">TYPE</span></span>|<span data-ttu-id="0e594-142">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-142">Int16</span></span>|
|<span data-ttu-id="0e594-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-144">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-144">Int16</span></span>|
|<span data-ttu-id="0e594-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-145">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-146">String</span><span class="sxs-lookup"><span data-stu-id="0e594-146">String</span></span>|
|<span data-ttu-id="0e594-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="0e594-147">ASC_OR_DESC</span></span>|<span data-ttu-id="0e594-148">String</span><span class="sxs-lookup"><span data-stu-id="0e594-148">String</span></span>|
|<span data-ttu-id="0e594-149">KARDYNALNOŚCI</span><span class="sxs-lookup"><span data-stu-id="0e594-149">CARDINALITY</span></span>|<span data-ttu-id="0e594-150">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-150">Int32</span></span>|
|<span data-ttu-id="0e594-151">PAGE</span><span class="sxs-lookup"><span data-stu-id="0e594-151">PAGES</span></span>|<span data-ttu-id="0e594-152">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-152">Int32</span></span>|
|<span data-ttu-id="0e594-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0e594-153">FILTER_CONDITION</span></span>|<span data-ttu-id="0e594-154">String</span><span class="sxs-lookup"><span data-stu-id="0e594-154">String</span></span>|
|<span data-ttu-id="0e594-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e594-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0e594-156">String</span><span class="sxs-lookup"><span data-stu-id="0e594-156">String</span></span>|
|<span data-ttu-id="0e594-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="0e594-158">Byte</span><span class="sxs-lookup"><span data-stu-id="0e594-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="0e594-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-159">Columns</span></span>

|<span data-ttu-id="0e594-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-160">ColumnName</span></span>|<span data-ttu-id="0e594-161">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-162">TABLE_CAT</span></span>|<span data-ttu-id="0e594-163">String</span><span class="sxs-lookup"><span data-stu-id="0e594-163">String</span></span>|
|<span data-ttu-id="0e594-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-164">TABLE_SCHEM</span></span>|<span data-ttu-id="0e594-165">String</span><span class="sxs-lookup"><span data-stu-id="0e594-165">String</span></span>|
|<span data-ttu-id="0e594-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-166">TABLE_NAME</span></span>|<span data-ttu-id="0e594-167">String</span><span class="sxs-lookup"><span data-stu-id="0e594-167">String</span></span>|
|<span data-ttu-id="0e594-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-168">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-169">String</span><span class="sxs-lookup"><span data-stu-id="0e594-169">String</span></span>|
|<span data-ttu-id="0e594-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-170">DATA_TYPE</span></span>|<span data-ttu-id="0e594-171">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-171">Int16</span></span>|
|<span data-ttu-id="0e594-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-172">TYPE_NAME</span></span>|<span data-ttu-id="0e594-173">String</span><span class="sxs-lookup"><span data-stu-id="0e594-173">String</span></span>|
|<span data-ttu-id="0e594-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e594-174">COLUMN_SIZE</span></span>|<span data-ttu-id="0e594-175">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-175">Int32</span></span>|
|<span data-ttu-id="0e594-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="0e594-177">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-177">Int32</span></span>|
|<span data-ttu-id="0e594-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0e594-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0e594-179">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-179">Int16</span></span>|
|<span data-ttu-id="0e594-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0e594-181">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-181">Int16</span></span>|
|<span data-ttu-id="0e594-182">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-182">NULLABLE</span></span>|<span data-ttu-id="0e594-183">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-183">Int16</span></span>|
|<span data-ttu-id="0e594-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-184">REMARKS</span></span>|<span data-ttu-id="0e594-185">String</span><span class="sxs-lookup"><span data-stu-id="0e594-185">String</span></span>|
|<span data-ttu-id="0e594-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0e594-186">COLUMN_DEF</span></span>|<span data-ttu-id="0e594-187">String</span><span class="sxs-lookup"><span data-stu-id="0e594-187">String</span></span>|
|<span data-ttu-id="0e594-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0e594-189">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-189">Int16</span></span>|
|<span data-ttu-id="0e594-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0e594-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0e594-191">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-191">Int16</span></span>|
|<span data-ttu-id="0e594-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0e594-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-193">Int32</span></span>|
|<span data-ttu-id="0e594-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-195">Int32</span></span>|
|<span data-ttu-id="0e594-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e594-196">IS_NULLABLE</span></span>|<span data-ttu-id="0e594-197">String</span><span class="sxs-lookup"><span data-stu-id="0e594-197">String</span></span>|
|<span data-ttu-id="0e594-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e594-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0e594-199">String</span><span class="sxs-lookup"><span data-stu-id="0e594-199">String</span></span>|
|<span data-ttu-id="0e594-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e594-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0e594-201">String</span><span class="sxs-lookup"><span data-stu-id="0e594-201">String</span></span>|
|<span data-ttu-id="0e594-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="0e594-203">Byte</span><span class="sxs-lookup"><span data-stu-id="0e594-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="0e594-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-204">Procedures</span></span>

|<span data-ttu-id="0e594-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-205">ColumnName</span></span>|<span data-ttu-id="0e594-206">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="0e594-208">String</span><span class="sxs-lookup"><span data-stu-id="0e594-208">String</span></span>|
|<span data-ttu-id="0e594-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0e594-210">String</span><span class="sxs-lookup"><span data-stu-id="0e594-210">String</span></span>|
|<span data-ttu-id="0e594-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-212">String</span><span class="sxs-lookup"><span data-stu-id="0e594-212">String</span></span>|
|<span data-ttu-id="0e594-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0e594-214">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-214">Int32</span></span>|
|<span data-ttu-id="0e594-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0e594-216">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-216">Int32</span></span>|
|<span data-ttu-id="0e594-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0e594-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0e594-218">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-218">Int32</span></span>|
|<span data-ttu-id="0e594-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-219">REMARKS</span></span>|<span data-ttu-id="0e594-220">String</span><span class="sxs-lookup"><span data-stu-id="0e594-220">String</span></span>|
|<span data-ttu-id="0e594-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e594-222">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="0e594-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-223">ProcedureColumns</span></span>

|<span data-ttu-id="0e594-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-224">ColumnName</span></span>|<span data-ttu-id="0e594-225">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="0e594-227">String</span><span class="sxs-lookup"><span data-stu-id="0e594-227">String</span></span>|
|<span data-ttu-id="0e594-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0e594-229">String</span><span class="sxs-lookup"><span data-stu-id="0e594-229">String</span></span>|
|<span data-ttu-id="0e594-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-231">String</span><span class="sxs-lookup"><span data-stu-id="0e594-231">String</span></span>|
|<span data-ttu-id="0e594-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-232">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-233">String</span><span class="sxs-lookup"><span data-stu-id="0e594-233">String</span></span>|
|<span data-ttu-id="0e594-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-234">COLUMN_TYPE</span></span>|<span data-ttu-id="0e594-235">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-235">Int16</span></span>|
|<span data-ttu-id="0e594-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-236">DATA_TYPE</span></span>|<span data-ttu-id="0e594-237">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-237">Int16</span></span>|
|<span data-ttu-id="0e594-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-238">TYPE_NAME</span></span>|<span data-ttu-id="0e594-239">String</span><span class="sxs-lookup"><span data-stu-id="0e594-239">String</span></span>|
|<span data-ttu-id="0e594-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e594-240">COLUMN_SIZE</span></span>|<span data-ttu-id="0e594-241">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-241">Int32</span></span>|
|<span data-ttu-id="0e594-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="0e594-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-243">Int32</span></span>|
|<span data-ttu-id="0e594-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0e594-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0e594-245">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-245">Int16</span></span>|
|<span data-ttu-id="0e594-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0e594-247">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-247">Int16</span></span>|
|<span data-ttu-id="0e594-248">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-248">NULLABLE</span></span>|<span data-ttu-id="0e594-249">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-249">Int16</span></span>|
|<span data-ttu-id="0e594-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-250">REMARKS</span></span>|<span data-ttu-id="0e594-251">String</span><span class="sxs-lookup"><span data-stu-id="0e594-251">String</span></span>|
|<span data-ttu-id="0e594-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0e594-252">COLUMN_DEF</span></span>|<span data-ttu-id="0e594-253">String</span><span class="sxs-lookup"><span data-stu-id="0e594-253">String</span></span>|
|<span data-ttu-id="0e594-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0e594-255">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-255">Int16</span></span>|
|<span data-ttu-id="0e594-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0e594-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0e594-257">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-257">Int16</span></span>|
|<span data-ttu-id="0e594-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0e594-259">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-259">Int32</span></span>|
|<span data-ttu-id="0e594-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-261">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-261">Int32</span></span>|
|<span data-ttu-id="0e594-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e594-262">IS_NULLABLE</span></span>|<span data-ttu-id="0e594-263">String</span><span class="sxs-lookup"><span data-stu-id="0e594-263">String</span></span>|
|<span data-ttu-id="0e594-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e594-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0e594-265">String</span><span class="sxs-lookup"><span data-stu-id="0e594-265">String</span></span>|
|<span data-ttu-id="0e594-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e594-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0e594-267">String</span><span class="sxs-lookup"><span data-stu-id="0e594-267">String</span></span>|
|<span data-ttu-id="0e594-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="0e594-269">Byte</span><span class="sxs-lookup"><span data-stu-id="0e594-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="0e594-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e594-270">ProcedureParameters</span></span>

|<span data-ttu-id="0e594-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-271">ColumnName</span></span>|<span data-ttu-id="0e594-272">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="0e594-274">String</span><span class="sxs-lookup"><span data-stu-id="0e594-274">String</span></span>|
|<span data-ttu-id="0e594-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0e594-276">String</span><span class="sxs-lookup"><span data-stu-id="0e594-276">String</span></span>|
|<span data-ttu-id="0e594-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-278">String</span><span class="sxs-lookup"><span data-stu-id="0e594-278">String</span></span>|
|<span data-ttu-id="0e594-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-279">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-280">String</span><span class="sxs-lookup"><span data-stu-id="0e594-280">String</span></span>|
|<span data-ttu-id="0e594-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-281">COLUMN_TYPE</span></span>|<span data-ttu-id="0e594-282">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-282">Int16</span></span>|
|<span data-ttu-id="0e594-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-283">DATA_TYPE</span></span>|<span data-ttu-id="0e594-284">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-284">Int16</span></span>|
|<span data-ttu-id="0e594-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-285">TYPE_NAME</span></span>|<span data-ttu-id="0e594-286">String</span><span class="sxs-lookup"><span data-stu-id="0e594-286">String</span></span>|
|<span data-ttu-id="0e594-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e594-287">COLUMN_SIZE</span></span>|<span data-ttu-id="0e594-288">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-288">Int32</span></span>|
|<span data-ttu-id="0e594-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="0e594-290">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-290">Int32</span></span>|
|<span data-ttu-id="0e594-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0e594-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0e594-292">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-292">Int16</span></span>|
|<span data-ttu-id="0e594-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0e594-294">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-294">Int16</span></span>|
|<span data-ttu-id="0e594-295">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-295">NULLABLE</span></span>|<span data-ttu-id="0e594-296">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-296">Int16</span></span>|
|<span data-ttu-id="0e594-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-297">REMARKS</span></span>|<span data-ttu-id="0e594-298">String</span><span class="sxs-lookup"><span data-stu-id="0e594-298">String</span></span>|
|<span data-ttu-id="0e594-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0e594-299">COLUMN_DEF</span></span>|<span data-ttu-id="0e594-300">String</span><span class="sxs-lookup"><span data-stu-id="0e594-300">String</span></span>|
|<span data-ttu-id="0e594-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0e594-302">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-302">Int16</span></span>|
|<span data-ttu-id="0e594-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0e594-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0e594-304">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-304">Int16</span></span>|
|<span data-ttu-id="0e594-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0e594-306">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-306">Int32</span></span>|
|<span data-ttu-id="0e594-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-308">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-308">Int32</span></span>|
|<span data-ttu-id="0e594-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e594-309">IS_NULLABLE</span></span>|<span data-ttu-id="0e594-310">String</span><span class="sxs-lookup"><span data-stu-id="0e594-310">String</span></span>|
|<span data-ttu-id="0e594-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0e594-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="0e594-312">String</span><span class="sxs-lookup"><span data-stu-id="0e594-312">String</span></span>|
|<span data-ttu-id="0e594-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0e594-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="0e594-314">String</span><span class="sxs-lookup"><span data-stu-id="0e594-314">String</span></span>|
|<span data-ttu-id="0e594-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="0e594-316">Byte</span><span class="sxs-lookup"><span data-stu-id="0e594-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="0e594-317">Sterownik Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="0e594-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="0e594-318">Microsoft SQL Server sterownik Oracle ODBC obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="0e594-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="0e594-319">Tabelę</span><span class="sxs-lookup"><span data-stu-id="0e594-319">Tables</span></span>

- <span data-ttu-id="0e594-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-320">Columns</span></span>

- <span data-ttu-id="0e594-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-321">Procedures</span></span>

- <span data-ttu-id="0e594-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-322">ProcedureColumns</span></span>

- <span data-ttu-id="0e594-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e594-323">ProcedureParameters</span></span>

- <span data-ttu-id="0e594-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-324">Views</span></span>

- <span data-ttu-id="0e594-325">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="0e594-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="0e594-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-326">Tables and Views</span></span>

|<span data-ttu-id="0e594-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-327">ColumnName</span></span>|<span data-ttu-id="0e594-328">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0e594-330">String</span><span class="sxs-lookup"><span data-stu-id="0e594-330">String</span></span>|
|<span data-ttu-id="0e594-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-331">TABLE_OWNER</span></span>|<span data-ttu-id="0e594-332">String</span><span class="sxs-lookup"><span data-stu-id="0e594-332">String</span></span>|
|<span data-ttu-id="0e594-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-333">TABLE_NAME</span></span>|<span data-ttu-id="0e594-334">String</span><span class="sxs-lookup"><span data-stu-id="0e594-334">String</span></span>|
|<span data-ttu-id="0e594-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-335">TABLE_TYPE</span></span>|<span data-ttu-id="0e594-336">String</span><span class="sxs-lookup"><span data-stu-id="0e594-336">String</span></span>|
|<span data-ttu-id="0e594-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-337">REMARKS</span></span>|<span data-ttu-id="0e594-338">String</span><span class="sxs-lookup"><span data-stu-id="0e594-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="0e594-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-339">Columns</span></span>

|<span data-ttu-id="0e594-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-340">ColumnName</span></span>|<span data-ttu-id="0e594-341">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0e594-343">String</span><span class="sxs-lookup"><span data-stu-id="0e594-343">String</span></span>|
|<span data-ttu-id="0e594-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-344">TABLE_OWNER</span></span>|<span data-ttu-id="0e594-345">String</span><span class="sxs-lookup"><span data-stu-id="0e594-345">String</span></span>|
|<span data-ttu-id="0e594-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-346">TABLE_NAME</span></span>|<span data-ttu-id="0e594-347">String</span><span class="sxs-lookup"><span data-stu-id="0e594-347">String</span></span>|
|<span data-ttu-id="0e594-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-348">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-349">String</span><span class="sxs-lookup"><span data-stu-id="0e594-349">String</span></span>|
|<span data-ttu-id="0e594-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-350">DATA_TYPE</span></span>|<span data-ttu-id="0e594-351">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-351">Int16</span></span>|
|<span data-ttu-id="0e594-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-352">TYPE_NAME</span></span>|<span data-ttu-id="0e594-353">String</span><span class="sxs-lookup"><span data-stu-id="0e594-353">String</span></span>|
|<span data-ttu-id="0e594-354">DOKŁADNE</span><span class="sxs-lookup"><span data-stu-id="0e594-354">PRECISION</span></span>|<span data-ttu-id="0e594-355">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-355">Int32</span></span>|
|<span data-ttu-id="0e594-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0e594-356">LENGTH</span></span>|<span data-ttu-id="0e594-357">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-357">Int32</span></span>|
|<span data-ttu-id="0e594-358">ZASIĘGU</span><span class="sxs-lookup"><span data-stu-id="0e594-358">SCALE</span></span>|<span data-ttu-id="0e594-359">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-359">Int16</span></span>|
|<span data-ttu-id="0e594-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-360">RADIX</span></span>|<span data-ttu-id="0e594-361">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-361">Int16</span></span>|
|<span data-ttu-id="0e594-362">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-362">NULLABLE</span></span>|<span data-ttu-id="0e594-363">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-363">Int16</span></span>|
|<span data-ttu-id="0e594-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-364">REMARKS</span></span>|<span data-ttu-id="0e594-365">String</span><span class="sxs-lookup"><span data-stu-id="0e594-365">String</span></span>|
|<span data-ttu-id="0e594-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-367">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="0e594-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-368">Procedures</span></span>

|<span data-ttu-id="0e594-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-369">ColumnName</span></span>|<span data-ttu-id="0e594-370">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0e594-372">String</span><span class="sxs-lookup"><span data-stu-id="0e594-372">String</span></span>|
|<span data-ttu-id="0e594-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0e594-374">String</span><span class="sxs-lookup"><span data-stu-id="0e594-374">String</span></span>|
|<span data-ttu-id="0e594-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-376">String</span><span class="sxs-lookup"><span data-stu-id="0e594-376">String</span></span>|
|<span data-ttu-id="0e594-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0e594-378">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-378">Int16</span></span>|
|<span data-ttu-id="0e594-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0e594-380">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-380">Int16</span></span>|
|<span data-ttu-id="0e594-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0e594-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0e594-382">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-382">Int16</span></span>|
|<span data-ttu-id="0e594-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-383">REMARKS</span></span>|<span data-ttu-id="0e594-384">String</span><span class="sxs-lookup"><span data-stu-id="0e594-384">String</span></span>|
|<span data-ttu-id="0e594-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e594-386">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="0e594-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-387">ProcedureColumns</span></span>

|<span data-ttu-id="0e594-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-388">ColumnName</span></span>|<span data-ttu-id="0e594-389">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0e594-391">String</span><span class="sxs-lookup"><span data-stu-id="0e594-391">String</span></span>|
|<span data-ttu-id="0e594-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0e594-393">String</span><span class="sxs-lookup"><span data-stu-id="0e594-393">String</span></span>|
|<span data-ttu-id="0e594-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-395">String</span><span class="sxs-lookup"><span data-stu-id="0e594-395">String</span></span>|
|<span data-ttu-id="0e594-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-396">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-397">String</span><span class="sxs-lookup"><span data-stu-id="0e594-397">String</span></span>|
|<span data-ttu-id="0e594-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-398">COLUMN_TYPE</span></span>|<span data-ttu-id="0e594-399">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-399">Int16</span></span>|
|<span data-ttu-id="0e594-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-400">DATA_TYPE</span></span>|<span data-ttu-id="0e594-401">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-401">Int16</span></span>|
|<span data-ttu-id="0e594-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-402">TYPE_NAME</span></span>|<span data-ttu-id="0e594-403">String</span><span class="sxs-lookup"><span data-stu-id="0e594-403">String</span></span>|
|<span data-ttu-id="0e594-404">DOKŁADNE</span><span class="sxs-lookup"><span data-stu-id="0e594-404">PRECISION</span></span>|<span data-ttu-id="0e594-405">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-405">Int32</span></span>|
|<span data-ttu-id="0e594-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0e594-406">LENGTH</span></span>|<span data-ttu-id="0e594-407">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-407">Int32</span></span>|
|<span data-ttu-id="0e594-408">ZASIĘGU</span><span class="sxs-lookup"><span data-stu-id="0e594-408">SCALE</span></span>|<span data-ttu-id="0e594-409">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-409">Int16</span></span>|
|<span data-ttu-id="0e594-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-410">RADIX</span></span>|<span data-ttu-id="0e594-411">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-411">Int16</span></span>|
|<span data-ttu-id="0e594-412">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-412">NULLABLE</span></span>|<span data-ttu-id="0e594-413">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-413">Int16</span></span>|
|<span data-ttu-id="0e594-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-414">REMARKS</span></span>|<span data-ttu-id="0e594-415">String</span><span class="sxs-lookup"><span data-stu-id="0e594-415">String</span></span>|
|<span data-ttu-id="0e594-416">WYSTĘPUJĄ</span><span class="sxs-lookup"><span data-stu-id="0e594-416">OVERLOAD</span></span>|<span data-ttu-id="0e594-417">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-417">Int32</span></span>|
|<span data-ttu-id="0e594-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-419">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="0e594-420">Sterownik Microsoft Jet ODBC</span><span class="sxs-lookup"><span data-stu-id="0e594-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="0e594-421">Sterownik Microsoft Jet ODBC obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="0e594-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="0e594-422">Tabelę</span><span class="sxs-lookup"><span data-stu-id="0e594-422">Tables</span></span>

- <span data-ttu-id="0e594-423">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="0e594-423">Indexes</span></span>

- <span data-ttu-id="0e594-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-424">Columns</span></span>

- <span data-ttu-id="0e594-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-425">Procedures</span></span>

- <span data-ttu-id="0e594-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-426">ProcedureColumns</span></span>

- <span data-ttu-id="0e594-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e594-427">ProcedureParameters</span></span>

- <span data-ttu-id="0e594-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="0e594-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="0e594-429">Tables and Views</span></span>

|<span data-ttu-id="0e594-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-430">ColumnName</span></span>|<span data-ttu-id="0e594-431">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0e594-433">String</span><span class="sxs-lookup"><span data-stu-id="0e594-433">String</span></span>|
|<span data-ttu-id="0e594-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-434">TABLE_OWNER</span></span>|<span data-ttu-id="0e594-435">String</span><span class="sxs-lookup"><span data-stu-id="0e594-435">String</span></span>|
|<span data-ttu-id="0e594-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-436">TABLE_NAME</span></span>|<span data-ttu-id="0e594-437">String</span><span class="sxs-lookup"><span data-stu-id="0e594-437">String</span></span>|
|<span data-ttu-id="0e594-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-438">TABLE_TYPE</span></span>|<span data-ttu-id="0e594-439">String</span><span class="sxs-lookup"><span data-stu-id="0e594-439">String</span></span>|
|<span data-ttu-id="0e594-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-440">REMARKS</span></span>|<span data-ttu-id="0e594-441">String</span><span class="sxs-lookup"><span data-stu-id="0e594-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="0e594-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0e594-442">Columns</span></span>

|<span data-ttu-id="0e594-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-443">ColumnName</span></span>|<span data-ttu-id="0e594-444">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="0e594-446">String</span><span class="sxs-lookup"><span data-stu-id="0e594-446">String</span></span>|
|<span data-ttu-id="0e594-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-447">TABLE_OWNER</span></span>|<span data-ttu-id="0e594-448">String</span><span class="sxs-lookup"><span data-stu-id="0e594-448">String</span></span>|
|<span data-ttu-id="0e594-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-449">TABLE_NAME</span></span>|<span data-ttu-id="0e594-450">String</span><span class="sxs-lookup"><span data-stu-id="0e594-450">String</span></span>|
|<span data-ttu-id="0e594-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-451">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-452">String</span><span class="sxs-lookup"><span data-stu-id="0e594-452">String</span></span>|
|<span data-ttu-id="0e594-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-453">DATA_TYPE</span></span>|<span data-ttu-id="0e594-454">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-454">Int16</span></span>|
|<span data-ttu-id="0e594-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-455">TYPE_NAME</span></span>|<span data-ttu-id="0e594-456">String</span><span class="sxs-lookup"><span data-stu-id="0e594-456">String</span></span>|
|<span data-ttu-id="0e594-457">DOKŁADNE</span><span class="sxs-lookup"><span data-stu-id="0e594-457">PRECISION</span></span>|<span data-ttu-id="0e594-458">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-458">Int32</span></span>|
|<span data-ttu-id="0e594-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0e594-459">LENGTH</span></span>|<span data-ttu-id="0e594-460">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-460">Int32</span></span>|
|<span data-ttu-id="0e594-461">ZASIĘGU</span><span class="sxs-lookup"><span data-stu-id="0e594-461">SCALE</span></span>|<span data-ttu-id="0e594-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-462">Int16</span></span>|
|<span data-ttu-id="0e594-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-463">RADIX</span></span>|<span data-ttu-id="0e594-464">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-464">Int16</span></span>|
|<span data-ttu-id="0e594-465">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-465">NULLABLE</span></span>|<span data-ttu-id="0e594-466">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-466">Int16</span></span>|
|<span data-ttu-id="0e594-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-467">REMARKS</span></span>|<span data-ttu-id="0e594-468">String</span><span class="sxs-lookup"><span data-stu-id="0e594-468">String</span></span>|
|<span data-ttu-id="0e594-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-470">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="0e594-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="0e594-471">Procedures</span></span>

|<span data-ttu-id="0e594-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-472">ColumnName</span></span>|<span data-ttu-id="0e594-473">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0e594-475">String</span><span class="sxs-lookup"><span data-stu-id="0e594-475">String</span></span>|
|<span data-ttu-id="0e594-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0e594-477">String</span><span class="sxs-lookup"><span data-stu-id="0e594-477">String</span></span>|
|<span data-ttu-id="0e594-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-479">String</span><span class="sxs-lookup"><span data-stu-id="0e594-479">String</span></span>|
|<span data-ttu-id="0e594-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="0e594-481">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-481">Int16</span></span>|
|<span data-ttu-id="0e594-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="0e594-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="0e594-483">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-483">Int16</span></span>|
|<span data-ttu-id="0e594-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="0e594-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="0e594-485">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-485">Int16</span></span>|
|<span data-ttu-id="0e594-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-486">REMARKS</span></span>|<span data-ttu-id="0e594-487">String</span><span class="sxs-lookup"><span data-stu-id="0e594-487">String</span></span>|
|<span data-ttu-id="0e594-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0e594-489">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="0e594-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0e594-490">ProcedureColumns</span></span>

|<span data-ttu-id="0e594-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-491">ColumnName</span></span>|<span data-ttu-id="0e594-492">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="0e594-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="0e594-494">String</span><span class="sxs-lookup"><span data-stu-id="0e594-494">String</span></span>|
|<span data-ttu-id="0e594-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e594-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="0e594-496">String</span><span class="sxs-lookup"><span data-stu-id="0e594-496">String</span></span>|
|<span data-ttu-id="0e594-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-498">String</span><span class="sxs-lookup"><span data-stu-id="0e594-498">String</span></span>|
|<span data-ttu-id="0e594-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-499">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-500">String</span><span class="sxs-lookup"><span data-stu-id="0e594-500">String</span></span>|
|<span data-ttu-id="0e594-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-501">COLUMN_TYPE</span></span>|<span data-ttu-id="0e594-502">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-502">Int16</span></span>|
|<span data-ttu-id="0e594-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-503">DATA_TYPE</span></span>|<span data-ttu-id="0e594-504">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-504">Int16</span></span>|
|<span data-ttu-id="0e594-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-505">TYPE_NAME</span></span>|<span data-ttu-id="0e594-506">String</span><span class="sxs-lookup"><span data-stu-id="0e594-506">String</span></span>|
|<span data-ttu-id="0e594-507">DOKŁADNE</span><span class="sxs-lookup"><span data-stu-id="0e594-507">PRECISION</span></span>|<span data-ttu-id="0e594-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-508">Int32</span></span>|
|<span data-ttu-id="0e594-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0e594-509">LENGTH</span></span>|<span data-ttu-id="0e594-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-510">Int32</span></span>|
|<span data-ttu-id="0e594-511">ZASIĘGU</span><span class="sxs-lookup"><span data-stu-id="0e594-511">SCALE</span></span>|<span data-ttu-id="0e594-512">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-512">Int16</span></span>|
|<span data-ttu-id="0e594-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-513">RADIX</span></span>|<span data-ttu-id="0e594-514">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-514">Int16</span></span>|
|<span data-ttu-id="0e594-515">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-515">NULLABLE</span></span>|<span data-ttu-id="0e594-516">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-516">Int16</span></span>|
|<span data-ttu-id="0e594-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-517">REMARKS</span></span>|<span data-ttu-id="0e594-518">String</span><span class="sxs-lookup"><span data-stu-id="0e594-518">String</span></span>|
|<span data-ttu-id="0e594-519">WYSTĘPUJĄ</span><span class="sxs-lookup"><span data-stu-id="0e594-519">OVERLOAD</span></span>|<span data-ttu-id="0e594-520">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-520">Int32</span></span>|
|<span data-ttu-id="0e594-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-522">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="0e594-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0e594-523">ProcedureParameters</span></span>

|<span data-ttu-id="0e594-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0e594-524">ColumnName</span></span>|<span data-ttu-id="0e594-525">DataType</span><span class="sxs-lookup"><span data-stu-id="0e594-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="0e594-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="0e594-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="0e594-527">String</span><span class="sxs-lookup"><span data-stu-id="0e594-527">String</span></span>|
|<span data-ttu-id="0e594-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="0e594-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="0e594-529">String</span><span class="sxs-lookup"><span data-stu-id="0e594-529">String</span></span>|
|<span data-ttu-id="0e594-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="0e594-531">String</span><span class="sxs-lookup"><span data-stu-id="0e594-531">String</span></span>|
|<span data-ttu-id="0e594-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-532">COLUMN_NAME</span></span>|<span data-ttu-id="0e594-533">String</span><span class="sxs-lookup"><span data-stu-id="0e594-533">String</span></span>|
|<span data-ttu-id="0e594-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-534">COLUMN_TYPE</span></span>|<span data-ttu-id="0e594-535">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-535">Int16</span></span>|
|<span data-ttu-id="0e594-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-536">DATA_TYPE</span></span>|<span data-ttu-id="0e594-537">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-537">Int16</span></span>|
|<span data-ttu-id="0e594-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0e594-538">TYPE_NAME</span></span>|<span data-ttu-id="0e594-539">String</span><span class="sxs-lookup"><span data-stu-id="0e594-539">String</span></span>|
|<span data-ttu-id="0e594-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="0e594-540">COLUMN_SIZE</span></span>|<span data-ttu-id="0e594-541">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-541">Int32</span></span>|
|<span data-ttu-id="0e594-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="0e594-543">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-543">Int32</span></span>|
|<span data-ttu-id="0e594-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="0e594-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="0e594-545">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-545">Int16</span></span>|
|<span data-ttu-id="0e594-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="0e594-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="0e594-547">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-547">Int16</span></span>|
|<span data-ttu-id="0e594-548">WYMAGA</span><span class="sxs-lookup"><span data-stu-id="0e594-548">NULLABLE</span></span>|<span data-ttu-id="0e594-549">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-549">Int16</span></span>|
|<span data-ttu-id="0e594-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="0e594-550">REMARKS</span></span>|<span data-ttu-id="0e594-551">String</span><span class="sxs-lookup"><span data-stu-id="0e594-551">String</span></span>|
|<span data-ttu-id="0e594-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="0e594-552">COLUMN_DEF</span></span>|<span data-ttu-id="0e594-553">String</span><span class="sxs-lookup"><span data-stu-id="0e594-553">String</span></span>|
|<span data-ttu-id="0e594-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0e594-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="0e594-555">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-555">Int16</span></span>|
|<span data-ttu-id="0e594-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="0e594-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="0e594-557">Int16</span><span class="sxs-lookup"><span data-stu-id="0e594-557">Int16</span></span>|
|<span data-ttu-id="0e594-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0e594-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="0e594-559">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-559">Int32</span></span>|
|<span data-ttu-id="0e594-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0e594-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="0e594-561">Int32</span><span class="sxs-lookup"><span data-stu-id="0e594-561">Int32</span></span>|
|<span data-ttu-id="0e594-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0e594-562">IS_NULLABLE</span></span>|<span data-ttu-id="0e594-563">String</span><span class="sxs-lookup"><span data-stu-id="0e594-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="0e594-564">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e594-564">See also</span></span>

- [<span data-ttu-id="0e594-565">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e594-565">ADO.NET Overview</span></span>](ado-net-overview.md)
