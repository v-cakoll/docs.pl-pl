---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772050"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="b5c14-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="b5c14-102">ODBC Schema Collections</span></span>

<span data-ttu-id="b5c14-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="b5c14-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="b5c14-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="b5c14-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="b5c14-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b5c14-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="b5c14-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="b5c14-106">Tables</span></span>

- <span data-ttu-id="b5c14-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b5c14-107">Indexes</span></span>

- <span data-ttu-id="b5c14-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-108">Columns</span></span>

- <span data-ttu-id="b5c14-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-109">Procedures</span></span>

- <span data-ttu-id="b5c14-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-110">ProcedureColumns</span></span>

- <span data-ttu-id="b5c14-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b5c14-111">ProcedureParameters</span></span>

- <span data-ttu-id="b5c14-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="b5c14-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-113">Tables and Views</span></span>

|<span data-ttu-id="b5c14-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-114">ColumnName</span></span>|<span data-ttu-id="b5c14-115">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-116">TABLE_CAT</span></span>|<span data-ttu-id="b5c14-117">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-117">String</span></span>|
|<span data-ttu-id="b5c14-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-118">TABLE_SCHEM</span></span>|<span data-ttu-id="b5c14-119">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-119">String</span></span>|
|<span data-ttu-id="b5c14-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-120">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-121">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-121">String</span></span>|
|<span data-ttu-id="b5c14-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-122">TABLE_TYPE</span></span>|<span data-ttu-id="b5c14-123">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-123">String</span></span>|
|<span data-ttu-id="b5c14-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-124">REMARKS</span></span>|<span data-ttu-id="b5c14-125">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="b5c14-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b5c14-126">Indexes</span></span>

|<span data-ttu-id="b5c14-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-127">ColumnName</span></span>|<span data-ttu-id="b5c14-128">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-129">TABLE_CAT</span></span>|<span data-ttu-id="b5c14-130">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-130">String</span></span>|
|<span data-ttu-id="b5c14-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-131">TABLE_SCHEM</span></span>|<span data-ttu-id="b5c14-132">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-132">String</span></span>|
|<span data-ttu-id="b5c14-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-133">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-134">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-134">String</span></span>|
|<span data-ttu-id="b5c14-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b5c14-135">NON_UNIQUE</span></span>|<span data-ttu-id="b5c14-136">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-136">Int16</span></span>|
|<span data-ttu-id="b5c14-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="b5c14-138">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-138">String</span></span>|
|<span data-ttu-id="b5c14-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-139">INDEX_NAME</span></span>|<span data-ttu-id="b5c14-140">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-140">String</span></span>|
|<span data-ttu-id="b5c14-141">TYP</span><span class="sxs-lookup"><span data-stu-id="b5c14-141">TYPE</span></span>|<span data-ttu-id="b5c14-142">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-142">Int16</span></span>|
|<span data-ttu-id="b5c14-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-144">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-144">Int16</span></span>|
|<span data-ttu-id="b5c14-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-145">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-146">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-146">String</span></span>|
|<span data-ttu-id="b5c14-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="b5c14-147">ASC_OR_DESC</span></span>|<span data-ttu-id="b5c14-148">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-148">String</span></span>|
|<span data-ttu-id="b5c14-149">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b5c14-149">CARDINALITY</span></span>|<span data-ttu-id="b5c14-150">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-150">Int32</span></span>|
|<span data-ttu-id="b5c14-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="b5c14-151">PAGES</span></span>|<span data-ttu-id="b5c14-152">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-152">Int32</span></span>|
|<span data-ttu-id="b5c14-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-153">FILTER_CONDITION</span></span>|<span data-ttu-id="b5c14-154">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-154">String</span></span>|
|<span data-ttu-id="b5c14-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b5c14-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b5c14-156">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-156">String</span></span>|
|<span data-ttu-id="b5c14-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-158">Byte</span><span class="sxs-lookup"><span data-stu-id="b5c14-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="b5c14-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-159">Columns</span></span>

|<span data-ttu-id="b5c14-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-160">ColumnName</span></span>|<span data-ttu-id="b5c14-161">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-162">TABLE_CAT</span></span>|<span data-ttu-id="b5c14-163">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-163">String</span></span>|
|<span data-ttu-id="b5c14-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-164">TABLE_SCHEM</span></span>|<span data-ttu-id="b5c14-165">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-165">String</span></span>|
|<span data-ttu-id="b5c14-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-166">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-167">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-167">String</span></span>|
|<span data-ttu-id="b5c14-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-168">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-169">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-169">String</span></span>|
|<span data-ttu-id="b5c14-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-170">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-171">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-171">Int16</span></span>|
|<span data-ttu-id="b5c14-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-172">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-173">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-173">String</span></span>|
|<span data-ttu-id="b5c14-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b5c14-174">COLUMN_SIZE</span></span>|<span data-ttu-id="b5c14-175">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-175">Int32</span></span>|
|<span data-ttu-id="b5c14-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="b5c14-177">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-177">Int32</span></span>|
|<span data-ttu-id="b5c14-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b5c14-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b5c14-179">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-179">Int16</span></span>|
|<span data-ttu-id="b5c14-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b5c14-181">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-181">Int16</span></span>|
|<span data-ttu-id="b5c14-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-182">NULLABLE</span></span>|<span data-ttu-id="b5c14-183">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-183">Int16</span></span>|
|<span data-ttu-id="b5c14-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-184">REMARKS</span></span>|<span data-ttu-id="b5c14-185">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-185">String</span></span>|
|<span data-ttu-id="b5c14-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b5c14-186">COLUMN_DEF</span></span>|<span data-ttu-id="b5c14-187">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-187">String</span></span>|
|<span data-ttu-id="b5c14-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-189">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-189">Int16</span></span>|
|<span data-ttu-id="b5c14-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b5c14-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b5c14-191">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-191">Int16</span></span>|
|<span data-ttu-id="b5c14-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b5c14-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-193">Int32</span></span>|
|<span data-ttu-id="b5c14-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-195">Int32</span></span>|
|<span data-ttu-id="b5c14-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-196">IS_NULLABLE</span></span>|<span data-ttu-id="b5c14-197">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-197">String</span></span>|
|<span data-ttu-id="b5c14-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b5c14-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b5c14-199">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-199">String</span></span>|
|<span data-ttu-id="b5c14-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b5c14-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b5c14-201">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-201">String</span></span>|
|<span data-ttu-id="b5c14-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-203">Byte</span><span class="sxs-lookup"><span data-stu-id="b5c14-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="b5c14-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-204">Procedures</span></span>

|<span data-ttu-id="b5c14-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-205">ColumnName</span></span>|<span data-ttu-id="b5c14-206">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="b5c14-208">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-208">String</span></span>|
|<span data-ttu-id="b5c14-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b5c14-210">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-210">String</span></span>|
|<span data-ttu-id="b5c14-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-212">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-212">String</span></span>|
|<span data-ttu-id="b5c14-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-214">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-214">Int32</span></span>|
|<span data-ttu-id="b5c14-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-216">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-216">Int32</span></span>|
|<span data-ttu-id="b5c14-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b5c14-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b5c14-218">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-218">Int32</span></span>|
|<span data-ttu-id="b5c14-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-219">REMARKS</span></span>|<span data-ttu-id="b5c14-220">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-220">String</span></span>|
|<span data-ttu-id="b5c14-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b5c14-222">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="b5c14-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-223">ProcedureColumns</span></span>

|<span data-ttu-id="b5c14-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-224">ColumnName</span></span>|<span data-ttu-id="b5c14-225">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="b5c14-227">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-227">String</span></span>|
|<span data-ttu-id="b5c14-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b5c14-229">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-229">String</span></span>|
|<span data-ttu-id="b5c14-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-231">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-231">String</span></span>|
|<span data-ttu-id="b5c14-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-232">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-233">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-233">String</span></span>|
|<span data-ttu-id="b5c14-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-234">COLUMN_TYPE</span></span>|<span data-ttu-id="b5c14-235">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-235">Int16</span></span>|
|<span data-ttu-id="b5c14-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-236">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-237">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-237">Int16</span></span>|
|<span data-ttu-id="b5c14-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-238">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-239">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-239">String</span></span>|
|<span data-ttu-id="b5c14-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b5c14-240">COLUMN_SIZE</span></span>|<span data-ttu-id="b5c14-241">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-241">Int32</span></span>|
|<span data-ttu-id="b5c14-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="b5c14-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-243">Int32</span></span>|
|<span data-ttu-id="b5c14-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b5c14-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b5c14-245">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-245">Int16</span></span>|
|<span data-ttu-id="b5c14-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b5c14-247">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-247">Int16</span></span>|
|<span data-ttu-id="b5c14-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-248">NULLABLE</span></span>|<span data-ttu-id="b5c14-249">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-249">Int16</span></span>|
|<span data-ttu-id="b5c14-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-250">REMARKS</span></span>|<span data-ttu-id="b5c14-251">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-251">String</span></span>|
|<span data-ttu-id="b5c14-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b5c14-252">COLUMN_DEF</span></span>|<span data-ttu-id="b5c14-253">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-253">String</span></span>|
|<span data-ttu-id="b5c14-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-255">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-255">Int16</span></span>|
|<span data-ttu-id="b5c14-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b5c14-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b5c14-257">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-257">Int16</span></span>|
|<span data-ttu-id="b5c14-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b5c14-259">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-259">Int32</span></span>|
|<span data-ttu-id="b5c14-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-261">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-261">Int32</span></span>|
|<span data-ttu-id="b5c14-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-262">IS_NULLABLE</span></span>|<span data-ttu-id="b5c14-263">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-263">String</span></span>|
|<span data-ttu-id="b5c14-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b5c14-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b5c14-265">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-265">String</span></span>|
|<span data-ttu-id="b5c14-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b5c14-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b5c14-267">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-267">String</span></span>|
|<span data-ttu-id="b5c14-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-269">Byte</span><span class="sxs-lookup"><span data-stu-id="b5c14-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="b5c14-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b5c14-270">ProcedureParameters</span></span>

|<span data-ttu-id="b5c14-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-271">ColumnName</span></span>|<span data-ttu-id="b5c14-272">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="b5c14-274">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-274">String</span></span>|
|<span data-ttu-id="b5c14-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b5c14-276">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-276">String</span></span>|
|<span data-ttu-id="b5c14-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-278">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-278">String</span></span>|
|<span data-ttu-id="b5c14-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-279">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-280">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-280">String</span></span>|
|<span data-ttu-id="b5c14-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-281">COLUMN_TYPE</span></span>|<span data-ttu-id="b5c14-282">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-282">Int16</span></span>|
|<span data-ttu-id="b5c14-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-283">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-284">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-284">Int16</span></span>|
|<span data-ttu-id="b5c14-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-285">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-286">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-286">String</span></span>|
|<span data-ttu-id="b5c14-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b5c14-287">COLUMN_SIZE</span></span>|<span data-ttu-id="b5c14-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-288">Int32</span></span>|
|<span data-ttu-id="b5c14-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="b5c14-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-290">Int32</span></span>|
|<span data-ttu-id="b5c14-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b5c14-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b5c14-292">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-292">Int16</span></span>|
|<span data-ttu-id="b5c14-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b5c14-294">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-294">Int16</span></span>|
|<span data-ttu-id="b5c14-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-295">NULLABLE</span></span>|<span data-ttu-id="b5c14-296">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-296">Int16</span></span>|
|<span data-ttu-id="b5c14-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-297">REMARKS</span></span>|<span data-ttu-id="b5c14-298">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-298">String</span></span>|
|<span data-ttu-id="b5c14-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b5c14-299">COLUMN_DEF</span></span>|<span data-ttu-id="b5c14-300">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-300">String</span></span>|
|<span data-ttu-id="b5c14-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-302">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-302">Int16</span></span>|
|<span data-ttu-id="b5c14-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b5c14-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b5c14-304">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-304">Int16</span></span>|
|<span data-ttu-id="b5c14-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b5c14-306">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-306">Int32</span></span>|
|<span data-ttu-id="b5c14-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-308">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-308">Int32</span></span>|
|<span data-ttu-id="b5c14-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-309">IS_NULLABLE</span></span>|<span data-ttu-id="b5c14-310">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-310">String</span></span>|
|<span data-ttu-id="b5c14-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b5c14-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b5c14-312">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-312">String</span></span>|
|<span data-ttu-id="b5c14-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b5c14-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b5c14-314">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-314">String</span></span>|
|<span data-ttu-id="b5c14-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-316">Byte</span><span class="sxs-lookup"><span data-stu-id="b5c14-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="b5c14-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="b5c14-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="b5c14-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b5c14-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="b5c14-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="b5c14-319">Tables</span></span>

- <span data-ttu-id="b5c14-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-320">Columns</span></span>

- <span data-ttu-id="b5c14-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-321">Procedures</span></span>

- <span data-ttu-id="b5c14-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-322">ProcedureColumns</span></span>

- <span data-ttu-id="b5c14-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b5c14-323">ProcedureParameters</span></span>

- <span data-ttu-id="b5c14-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-324">Views</span></span>

- <span data-ttu-id="b5c14-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b5c14-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="b5c14-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-326">Tables and Views</span></span>

|<span data-ttu-id="b5c14-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-327">ColumnName</span></span>|<span data-ttu-id="b5c14-328">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-330">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-330">String</span></span>|
|<span data-ttu-id="b5c14-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-331">TABLE_OWNER</span></span>|<span data-ttu-id="b5c14-332">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-332">String</span></span>|
|<span data-ttu-id="b5c14-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-333">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-334">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-334">String</span></span>|
|<span data-ttu-id="b5c14-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-335">TABLE_TYPE</span></span>|<span data-ttu-id="b5c14-336">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-336">String</span></span>|
|<span data-ttu-id="b5c14-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-337">REMARKS</span></span>|<span data-ttu-id="b5c14-338">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="b5c14-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-339">Columns</span></span>

|<span data-ttu-id="b5c14-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-340">ColumnName</span></span>|<span data-ttu-id="b5c14-341">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-343">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-343">String</span></span>|
|<span data-ttu-id="b5c14-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-344">TABLE_OWNER</span></span>|<span data-ttu-id="b5c14-345">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-345">String</span></span>|
|<span data-ttu-id="b5c14-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-346">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-347">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-347">String</span></span>|
|<span data-ttu-id="b5c14-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-348">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-349">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-349">String</span></span>|
|<span data-ttu-id="b5c14-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-350">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-351">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-351">Int16</span></span>|
|<span data-ttu-id="b5c14-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-352">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-353">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-353">String</span></span>|
|<span data-ttu-id="b5c14-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="b5c14-354">PRECISION</span></span>|<span data-ttu-id="b5c14-355">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-355">Int32</span></span>|
|<span data-ttu-id="b5c14-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b5c14-356">LENGTH</span></span>|<span data-ttu-id="b5c14-357">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-357">Int32</span></span>|
|<span data-ttu-id="b5c14-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="b5c14-358">SCALE</span></span>|<span data-ttu-id="b5c14-359">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-359">Int16</span></span>|
|<span data-ttu-id="b5c14-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-360">RADIX</span></span>|<span data-ttu-id="b5c14-361">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-361">Int16</span></span>|
|<span data-ttu-id="b5c14-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-362">NULLABLE</span></span>|<span data-ttu-id="b5c14-363">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-363">Int16</span></span>|
|<span data-ttu-id="b5c14-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-364">REMARKS</span></span>|<span data-ttu-id="b5c14-365">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-365">String</span></span>|
|<span data-ttu-id="b5c14-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-367">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="b5c14-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-368">Procedures</span></span>

|<span data-ttu-id="b5c14-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-369">ColumnName</span></span>|<span data-ttu-id="b5c14-370">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-372">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-372">String</span></span>|
|<span data-ttu-id="b5c14-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b5c14-374">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-374">String</span></span>|
|<span data-ttu-id="b5c14-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-376">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-376">String</span></span>|
|<span data-ttu-id="b5c14-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-378">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-378">Int16</span></span>|
|<span data-ttu-id="b5c14-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-380">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-380">Int16</span></span>|
|<span data-ttu-id="b5c14-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b5c14-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b5c14-382">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-382">Int16</span></span>|
|<span data-ttu-id="b5c14-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-383">REMARKS</span></span>|<span data-ttu-id="b5c14-384">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-384">String</span></span>|
|<span data-ttu-id="b5c14-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b5c14-386">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="b5c14-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-387">ProcedureColumns</span></span>

|<span data-ttu-id="b5c14-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-388">ColumnName</span></span>|<span data-ttu-id="b5c14-389">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-391">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-391">String</span></span>|
|<span data-ttu-id="b5c14-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b5c14-393">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-393">String</span></span>|
|<span data-ttu-id="b5c14-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-395">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-395">String</span></span>|
|<span data-ttu-id="b5c14-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-396">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-397">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-397">String</span></span>|
|<span data-ttu-id="b5c14-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-398">COLUMN_TYPE</span></span>|<span data-ttu-id="b5c14-399">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-399">Int16</span></span>|
|<span data-ttu-id="b5c14-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-400">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-401">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-401">Int16</span></span>|
|<span data-ttu-id="b5c14-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-402">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-403">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-403">String</span></span>|
|<span data-ttu-id="b5c14-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="b5c14-404">PRECISION</span></span>|<span data-ttu-id="b5c14-405">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-405">Int32</span></span>|
|<span data-ttu-id="b5c14-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b5c14-406">LENGTH</span></span>|<span data-ttu-id="b5c14-407">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-407">Int32</span></span>|
|<span data-ttu-id="b5c14-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="b5c14-408">SCALE</span></span>|<span data-ttu-id="b5c14-409">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-409">Int16</span></span>|
|<span data-ttu-id="b5c14-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-410">RADIX</span></span>|<span data-ttu-id="b5c14-411">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-411">Int16</span></span>|
|<span data-ttu-id="b5c14-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-412">NULLABLE</span></span>|<span data-ttu-id="b5c14-413">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-413">Int16</span></span>|
|<span data-ttu-id="b5c14-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-414">REMARKS</span></span>|<span data-ttu-id="b5c14-415">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-415">String</span></span>|
|<span data-ttu-id="b5c14-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="b5c14-416">OVERLOAD</span></span>|<span data-ttu-id="b5c14-417">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-417">Int32</span></span>|
|<span data-ttu-id="b5c14-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-419">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="b5c14-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="b5c14-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="b5c14-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b5c14-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="b5c14-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="b5c14-422">Tables</span></span>

- <span data-ttu-id="b5c14-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b5c14-423">Indexes</span></span>

- <span data-ttu-id="b5c14-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-424">Columns</span></span>

- <span data-ttu-id="b5c14-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-425">Procedures</span></span>

- <span data-ttu-id="b5c14-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-426">ProcedureColumns</span></span>

- <span data-ttu-id="b5c14-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b5c14-427">ProcedureParameters</span></span>

- <span data-ttu-id="b5c14-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="b5c14-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b5c14-429">Tables and Views</span></span>

|<span data-ttu-id="b5c14-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-430">ColumnName</span></span>|<span data-ttu-id="b5c14-431">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-433">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-433">String</span></span>|
|<span data-ttu-id="b5c14-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-434">TABLE_OWNER</span></span>|<span data-ttu-id="b5c14-435">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-435">String</span></span>|
|<span data-ttu-id="b5c14-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-436">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-437">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-437">String</span></span>|
|<span data-ttu-id="b5c14-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-438">TABLE_TYPE</span></span>|<span data-ttu-id="b5c14-439">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-439">String</span></span>|
|<span data-ttu-id="b5c14-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-440">REMARKS</span></span>|<span data-ttu-id="b5c14-441">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="b5c14-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-442">Columns</span></span>

|<span data-ttu-id="b5c14-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-443">ColumnName</span></span>|<span data-ttu-id="b5c14-444">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-446">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-446">String</span></span>|
|<span data-ttu-id="b5c14-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-447">TABLE_OWNER</span></span>|<span data-ttu-id="b5c14-448">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-448">String</span></span>|
|<span data-ttu-id="b5c14-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-449">TABLE_NAME</span></span>|<span data-ttu-id="b5c14-450">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-450">String</span></span>|
|<span data-ttu-id="b5c14-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-451">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-452">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-452">String</span></span>|
|<span data-ttu-id="b5c14-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-453">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-454">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-454">Int16</span></span>|
|<span data-ttu-id="b5c14-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-455">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-456">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-456">String</span></span>|
|<span data-ttu-id="b5c14-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="b5c14-457">PRECISION</span></span>|<span data-ttu-id="b5c14-458">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-458">Int32</span></span>|
|<span data-ttu-id="b5c14-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b5c14-459">LENGTH</span></span>|<span data-ttu-id="b5c14-460">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-460">Int32</span></span>|
|<span data-ttu-id="b5c14-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="b5c14-461">SCALE</span></span>|<span data-ttu-id="b5c14-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-462">Int16</span></span>|
|<span data-ttu-id="b5c14-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-463">RADIX</span></span>|<span data-ttu-id="b5c14-464">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-464">Int16</span></span>|
|<span data-ttu-id="b5c14-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-465">NULLABLE</span></span>|<span data-ttu-id="b5c14-466">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-466">Int16</span></span>|
|<span data-ttu-id="b5c14-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-467">REMARKS</span></span>|<span data-ttu-id="b5c14-468">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-468">String</span></span>|
|<span data-ttu-id="b5c14-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-470">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="b5c14-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5c14-471">Procedures</span></span>

|<span data-ttu-id="b5c14-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-472">ColumnName</span></span>|<span data-ttu-id="b5c14-473">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-475">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-475">String</span></span>|
|<span data-ttu-id="b5c14-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b5c14-477">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-477">String</span></span>|
|<span data-ttu-id="b5c14-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-479">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-479">String</span></span>|
|<span data-ttu-id="b5c14-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-481">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-481">Int16</span></span>|
|<span data-ttu-id="b5c14-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b5c14-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b5c14-483">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-483">Int16</span></span>|
|<span data-ttu-id="b5c14-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b5c14-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b5c14-485">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-485">Int16</span></span>|
|<span data-ttu-id="b5c14-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-486">REMARKS</span></span>|<span data-ttu-id="b5c14-487">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-487">String</span></span>|
|<span data-ttu-id="b5c14-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b5c14-489">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="b5c14-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b5c14-490">ProcedureColumns</span></span>

|<span data-ttu-id="b5c14-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-491">ColumnName</span></span>|<span data-ttu-id="b5c14-492">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b5c14-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b5c14-494">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-494">String</span></span>|
|<span data-ttu-id="b5c14-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5c14-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b5c14-496">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-496">String</span></span>|
|<span data-ttu-id="b5c14-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-498">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-498">String</span></span>|
|<span data-ttu-id="b5c14-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-499">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-500">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-500">String</span></span>|
|<span data-ttu-id="b5c14-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-501">COLUMN_TYPE</span></span>|<span data-ttu-id="b5c14-502">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-502">Int16</span></span>|
|<span data-ttu-id="b5c14-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-503">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-504">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-504">Int16</span></span>|
|<span data-ttu-id="b5c14-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-505">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-506">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-506">String</span></span>|
|<span data-ttu-id="b5c14-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="b5c14-507">PRECISION</span></span>|<span data-ttu-id="b5c14-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-508">Int32</span></span>|
|<span data-ttu-id="b5c14-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b5c14-509">LENGTH</span></span>|<span data-ttu-id="b5c14-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-510">Int32</span></span>|
|<span data-ttu-id="b5c14-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="b5c14-511">SCALE</span></span>|<span data-ttu-id="b5c14-512">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-512">Int16</span></span>|
|<span data-ttu-id="b5c14-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-513">RADIX</span></span>|<span data-ttu-id="b5c14-514">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-514">Int16</span></span>|
|<span data-ttu-id="b5c14-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-515">NULLABLE</span></span>|<span data-ttu-id="b5c14-516">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-516">Int16</span></span>|
|<span data-ttu-id="b5c14-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-517">REMARKS</span></span>|<span data-ttu-id="b5c14-518">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-518">String</span></span>|
|<span data-ttu-id="b5c14-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="b5c14-519">OVERLOAD</span></span>|<span data-ttu-id="b5c14-520">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-520">Int32</span></span>|
|<span data-ttu-id="b5c14-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-522">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="b5c14-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b5c14-523">ProcedureParameters</span></span>

|<span data-ttu-id="b5c14-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b5c14-524">ColumnName</span></span>|<span data-ttu-id="b5c14-525">DataType</span><span class="sxs-lookup"><span data-stu-id="b5c14-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="b5c14-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b5c14-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="b5c14-527">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-527">String</span></span>|
|<span data-ttu-id="b5c14-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b5c14-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b5c14-529">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-529">String</span></span>|
|<span data-ttu-id="b5c14-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="b5c14-531">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-531">String</span></span>|
|<span data-ttu-id="b5c14-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-532">COLUMN_NAME</span></span>|<span data-ttu-id="b5c14-533">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-533">String</span></span>|
|<span data-ttu-id="b5c14-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-534">COLUMN_TYPE</span></span>|<span data-ttu-id="b5c14-535">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-535">Int16</span></span>|
|<span data-ttu-id="b5c14-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-536">DATA_TYPE</span></span>|<span data-ttu-id="b5c14-537">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-537">Int16</span></span>|
|<span data-ttu-id="b5c14-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b5c14-538">TYPE_NAME</span></span>|<span data-ttu-id="b5c14-539">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-539">String</span></span>|
|<span data-ttu-id="b5c14-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b5c14-540">COLUMN_SIZE</span></span>|<span data-ttu-id="b5c14-541">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-541">Int32</span></span>|
|<span data-ttu-id="b5c14-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="b5c14-543">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-543">Int32</span></span>|
|<span data-ttu-id="b5c14-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b5c14-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b5c14-545">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-545">Int16</span></span>|
|<span data-ttu-id="b5c14-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b5c14-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b5c14-547">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-547">Int16</span></span>|
|<span data-ttu-id="b5c14-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-548">NULLABLE</span></span>|<span data-ttu-id="b5c14-549">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-549">Int16</span></span>|
|<span data-ttu-id="b5c14-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b5c14-550">REMARKS</span></span>|<span data-ttu-id="b5c14-551">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-551">String</span></span>|
|<span data-ttu-id="b5c14-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b5c14-552">COLUMN_DEF</span></span>|<span data-ttu-id="b5c14-553">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-553">String</span></span>|
|<span data-ttu-id="b5c14-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b5c14-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b5c14-555">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-555">Int16</span></span>|
|<span data-ttu-id="b5c14-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b5c14-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b5c14-557">Int16</span><span class="sxs-lookup"><span data-stu-id="b5c14-557">Int16</span></span>|
|<span data-ttu-id="b5c14-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b5c14-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b5c14-559">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-559">Int32</span></span>|
|<span data-ttu-id="b5c14-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b5c14-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="b5c14-561">Int32</span><span class="sxs-lookup"><span data-stu-id="b5c14-561">Int32</span></span>|
|<span data-ttu-id="b5c14-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b5c14-562">IS_NULLABLE</span></span>|<span data-ttu-id="b5c14-563">String</span><span class="sxs-lookup"><span data-stu-id="b5c14-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="b5c14-564">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5c14-564">See also</span></span>

- [<span data-ttu-id="b5c14-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b5c14-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
