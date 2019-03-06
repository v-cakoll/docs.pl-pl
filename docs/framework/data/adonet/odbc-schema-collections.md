---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: ffe80120ceffbe29c0a117cf1194860c5782be8c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365909"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="e6dee-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="e6dee-102">ODBC Schema Collections</span></span>

<span data-ttu-id="e6dee-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="e6dee-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="e6dee-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="e6dee-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="e6dee-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="e6dee-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e6dee-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="e6dee-106">Tables</span></span>

- <span data-ttu-id="e6dee-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="e6dee-107">Indexes</span></span>

- <span data-ttu-id="e6dee-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-108">Columns</span></span>

- <span data-ttu-id="e6dee-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-109">Procedures</span></span>

- <span data-ttu-id="e6dee-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-110">ProcedureColumns</span></span>

- <span data-ttu-id="e6dee-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6dee-111">ProcedureParameters</span></span>

- <span data-ttu-id="e6dee-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e6dee-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-113">Tables and Views</span></span>

|<span data-ttu-id="e6dee-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-114">ColumnName</span></span>|<span data-ttu-id="e6dee-115">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-116">TABLE_CAT</span></span>|<span data-ttu-id="e6dee-117">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-117">String</span></span>|
|<span data-ttu-id="e6dee-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-118">TABLE_SCHEM</span></span>|<span data-ttu-id="e6dee-119">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-119">String</span></span>|
|<span data-ttu-id="e6dee-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-120">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-121">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-121">String</span></span>|
|<span data-ttu-id="e6dee-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-122">TABLE_TYPE</span></span>|<span data-ttu-id="e6dee-123">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-123">String</span></span>|
|<span data-ttu-id="e6dee-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-124">REMARKS</span></span>|<span data-ttu-id="e6dee-125">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="e6dee-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="e6dee-126">Indexes</span></span>

|<span data-ttu-id="e6dee-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-127">ColumnName</span></span>|<span data-ttu-id="e6dee-128">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-129">TABLE_CAT</span></span>|<span data-ttu-id="e6dee-130">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-130">String</span></span>|
|<span data-ttu-id="e6dee-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-131">TABLE_SCHEM</span></span>|<span data-ttu-id="e6dee-132">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-132">String</span></span>|
|<span data-ttu-id="e6dee-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-133">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-134">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-134">String</span></span>|
|<span data-ttu-id="e6dee-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e6dee-135">NON_UNIQUE</span></span>|<span data-ttu-id="e6dee-136">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-136">Int16</span></span>|
|<span data-ttu-id="e6dee-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="e6dee-138">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-138">String</span></span>|
|<span data-ttu-id="e6dee-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-139">INDEX_NAME</span></span>|<span data-ttu-id="e6dee-140">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-140">String</span></span>|
|<span data-ttu-id="e6dee-141">TYP</span><span class="sxs-lookup"><span data-stu-id="e6dee-141">TYPE</span></span>|<span data-ttu-id="e6dee-142">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-142">Int16</span></span>|
|<span data-ttu-id="e6dee-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-144">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-144">Int16</span></span>|
|<span data-ttu-id="e6dee-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-145">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-146">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-146">String</span></span>|
|<span data-ttu-id="e6dee-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="e6dee-147">ASC_OR_DESC</span></span>|<span data-ttu-id="e6dee-148">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-148">String</span></span>|
|<span data-ttu-id="e6dee-149">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e6dee-149">CARDINALITY</span></span>|<span data-ttu-id="e6dee-150">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-150">Int32</span></span>|
|<span data-ttu-id="e6dee-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="e6dee-151">PAGES</span></span>|<span data-ttu-id="e6dee-152">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-152">Int32</span></span>|
|<span data-ttu-id="e6dee-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-153">FILTER_CONDITION</span></span>|<span data-ttu-id="e6dee-154">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-154">String</span></span>|
|<span data-ttu-id="e6dee-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6dee-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6dee-156">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-156">String</span></span>|
|<span data-ttu-id="e6dee-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-158">Byte</span><span class="sxs-lookup"><span data-stu-id="e6dee-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="e6dee-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-159">Columns</span></span>

|<span data-ttu-id="e6dee-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-160">ColumnName</span></span>|<span data-ttu-id="e6dee-161">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-162">TABLE_CAT</span></span>|<span data-ttu-id="e6dee-163">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-163">String</span></span>|
|<span data-ttu-id="e6dee-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-164">TABLE_SCHEM</span></span>|<span data-ttu-id="e6dee-165">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-165">String</span></span>|
|<span data-ttu-id="e6dee-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-166">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-167">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-167">String</span></span>|
|<span data-ttu-id="e6dee-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-168">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-169">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-169">String</span></span>|
|<span data-ttu-id="e6dee-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-170">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-171">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-171">Int16</span></span>|
|<span data-ttu-id="e6dee-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-172">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-173">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-173">String</span></span>|
|<span data-ttu-id="e6dee-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6dee-174">COLUMN_SIZE</span></span>|<span data-ttu-id="e6dee-175">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-175">Int32</span></span>|
|<span data-ttu-id="e6dee-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6dee-177">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-177">Int32</span></span>|
|<span data-ttu-id="e6dee-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6dee-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6dee-179">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-179">Int16</span></span>|
|<span data-ttu-id="e6dee-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6dee-181">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-181">Int16</span></span>|
|<span data-ttu-id="e6dee-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-182">NULLABLE</span></span>|<span data-ttu-id="e6dee-183">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-183">Int16</span></span>|
|<span data-ttu-id="e6dee-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-184">REMARKS</span></span>|<span data-ttu-id="e6dee-185">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-185">String</span></span>|
|<span data-ttu-id="e6dee-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6dee-186">COLUMN_DEF</span></span>|<span data-ttu-id="e6dee-187">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-187">String</span></span>|
|<span data-ttu-id="e6dee-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-189">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-189">Int16</span></span>|
|<span data-ttu-id="e6dee-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6dee-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6dee-191">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-191">Int16</span></span>|
|<span data-ttu-id="e6dee-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6dee-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-193">Int32</span></span>|
|<span data-ttu-id="e6dee-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-195">Int32</span></span>|
|<span data-ttu-id="e6dee-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-196">IS_NULLABLE</span></span>|<span data-ttu-id="e6dee-197">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-197">String</span></span>|
|<span data-ttu-id="e6dee-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6dee-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6dee-199">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-199">String</span></span>|
|<span data-ttu-id="e6dee-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6dee-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6dee-201">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-201">String</span></span>|
|<span data-ttu-id="e6dee-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-203">Byte</span><span class="sxs-lookup"><span data-stu-id="e6dee-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="e6dee-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-204">Procedures</span></span>

|<span data-ttu-id="e6dee-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-205">ColumnName</span></span>|<span data-ttu-id="e6dee-206">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6dee-208">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-208">String</span></span>|
|<span data-ttu-id="e6dee-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6dee-210">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-210">String</span></span>|
|<span data-ttu-id="e6dee-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-212">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-212">String</span></span>|
|<span data-ttu-id="e6dee-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-214">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-214">Int32</span></span>|
|<span data-ttu-id="e6dee-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-216">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-216">Int32</span></span>|
|<span data-ttu-id="e6dee-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6dee-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6dee-218">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-218">Int32</span></span>|
|<span data-ttu-id="e6dee-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-219">REMARKS</span></span>|<span data-ttu-id="e6dee-220">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-220">String</span></span>|
|<span data-ttu-id="e6dee-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6dee-222">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e6dee-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-223">ProcedureColumns</span></span>

|<span data-ttu-id="e6dee-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-224">ColumnName</span></span>|<span data-ttu-id="e6dee-225">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6dee-227">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-227">String</span></span>|
|<span data-ttu-id="e6dee-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6dee-229">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-229">String</span></span>|
|<span data-ttu-id="e6dee-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-231">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-231">String</span></span>|
|<span data-ttu-id="e6dee-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-232">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-233">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-233">String</span></span>|
|<span data-ttu-id="e6dee-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-234">COLUMN_TYPE</span></span>|<span data-ttu-id="e6dee-235">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-235">Int16</span></span>|
|<span data-ttu-id="e6dee-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-236">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-237">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-237">Int16</span></span>|
|<span data-ttu-id="e6dee-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-238">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-239">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-239">String</span></span>|
|<span data-ttu-id="e6dee-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6dee-240">COLUMN_SIZE</span></span>|<span data-ttu-id="e6dee-241">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-241">Int32</span></span>|
|<span data-ttu-id="e6dee-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6dee-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-243">Int32</span></span>|
|<span data-ttu-id="e6dee-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6dee-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6dee-245">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-245">Int16</span></span>|
|<span data-ttu-id="e6dee-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6dee-247">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-247">Int16</span></span>|
|<span data-ttu-id="e6dee-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-248">NULLABLE</span></span>|<span data-ttu-id="e6dee-249">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-249">Int16</span></span>|
|<span data-ttu-id="e6dee-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-250">REMARKS</span></span>|<span data-ttu-id="e6dee-251">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-251">String</span></span>|
|<span data-ttu-id="e6dee-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6dee-252">COLUMN_DEF</span></span>|<span data-ttu-id="e6dee-253">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-253">String</span></span>|
|<span data-ttu-id="e6dee-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-255">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-255">Int16</span></span>|
|<span data-ttu-id="e6dee-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6dee-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6dee-257">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-257">Int16</span></span>|
|<span data-ttu-id="e6dee-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6dee-259">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-259">Int32</span></span>|
|<span data-ttu-id="e6dee-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-261">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-261">Int32</span></span>|
|<span data-ttu-id="e6dee-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-262">IS_NULLABLE</span></span>|<span data-ttu-id="e6dee-263">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-263">String</span></span>|
|<span data-ttu-id="e6dee-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6dee-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6dee-265">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-265">String</span></span>|
|<span data-ttu-id="e6dee-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6dee-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6dee-267">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-267">String</span></span>|
|<span data-ttu-id="e6dee-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-269">Byte</span><span class="sxs-lookup"><span data-stu-id="e6dee-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="e6dee-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6dee-270">ProcedureParameters</span></span>

|<span data-ttu-id="e6dee-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-271">ColumnName</span></span>|<span data-ttu-id="e6dee-272">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6dee-274">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-274">String</span></span>|
|<span data-ttu-id="e6dee-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6dee-276">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-276">String</span></span>|
|<span data-ttu-id="e6dee-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-278">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-278">String</span></span>|
|<span data-ttu-id="e6dee-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-279">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-280">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-280">String</span></span>|
|<span data-ttu-id="e6dee-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-281">COLUMN_TYPE</span></span>|<span data-ttu-id="e6dee-282">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-282">Int16</span></span>|
|<span data-ttu-id="e6dee-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-283">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-284">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-284">Int16</span></span>|
|<span data-ttu-id="e6dee-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-285">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-286">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-286">String</span></span>|
|<span data-ttu-id="e6dee-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6dee-287">COLUMN_SIZE</span></span>|<span data-ttu-id="e6dee-288">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-288">Int32</span></span>|
|<span data-ttu-id="e6dee-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6dee-290">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-290">Int32</span></span>|
|<span data-ttu-id="e6dee-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6dee-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6dee-292">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-292">Int16</span></span>|
|<span data-ttu-id="e6dee-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6dee-294">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-294">Int16</span></span>|
|<span data-ttu-id="e6dee-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-295">NULLABLE</span></span>|<span data-ttu-id="e6dee-296">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-296">Int16</span></span>|
|<span data-ttu-id="e6dee-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-297">REMARKS</span></span>|<span data-ttu-id="e6dee-298">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-298">String</span></span>|
|<span data-ttu-id="e6dee-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6dee-299">COLUMN_DEF</span></span>|<span data-ttu-id="e6dee-300">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-300">String</span></span>|
|<span data-ttu-id="e6dee-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-302">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-302">Int16</span></span>|
|<span data-ttu-id="e6dee-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6dee-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6dee-304">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-304">Int16</span></span>|
|<span data-ttu-id="e6dee-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6dee-306">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-306">Int32</span></span>|
|<span data-ttu-id="e6dee-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-308">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-308">Int32</span></span>|
|<span data-ttu-id="e6dee-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-309">IS_NULLABLE</span></span>|<span data-ttu-id="e6dee-310">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-310">String</span></span>|
|<span data-ttu-id="e6dee-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e6dee-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="e6dee-312">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-312">String</span></span>|
|<span data-ttu-id="e6dee-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e6dee-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="e6dee-314">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-314">String</span></span>|
|<span data-ttu-id="e6dee-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-316">Byte</span><span class="sxs-lookup"><span data-stu-id="e6dee-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="e6dee-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e6dee-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="e6dee-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="e6dee-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e6dee-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="e6dee-319">Tables</span></span>

- <span data-ttu-id="e6dee-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-320">Columns</span></span>

- <span data-ttu-id="e6dee-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-321">Procedures</span></span>

- <span data-ttu-id="e6dee-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-322">ProcedureColumns</span></span>

- <span data-ttu-id="e6dee-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6dee-323">ProcedureParameters</span></span>

- <span data-ttu-id="e6dee-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-324">Views</span></span>

- <span data-ttu-id="e6dee-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="e6dee-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e6dee-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-326">Tables and Views</span></span>

|<span data-ttu-id="e6dee-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-327">ColumnName</span></span>|<span data-ttu-id="e6dee-328">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-330">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-330">String</span></span>|
|<span data-ttu-id="e6dee-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-331">TABLE_OWNER</span></span>|<span data-ttu-id="e6dee-332">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-332">String</span></span>|
|<span data-ttu-id="e6dee-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-333">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-334">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-334">String</span></span>|
|<span data-ttu-id="e6dee-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-335">TABLE_TYPE</span></span>|<span data-ttu-id="e6dee-336">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-336">String</span></span>|
|<span data-ttu-id="e6dee-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-337">REMARKS</span></span>|<span data-ttu-id="e6dee-338">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="e6dee-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-339">Columns</span></span>

|<span data-ttu-id="e6dee-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-340">ColumnName</span></span>|<span data-ttu-id="e6dee-341">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-343">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-343">String</span></span>|
|<span data-ttu-id="e6dee-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-344">TABLE_OWNER</span></span>|<span data-ttu-id="e6dee-345">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-345">String</span></span>|
|<span data-ttu-id="e6dee-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-346">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-347">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-347">String</span></span>|
|<span data-ttu-id="e6dee-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-348">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-349">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-349">String</span></span>|
|<span data-ttu-id="e6dee-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-350">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-351">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-351">Int16</span></span>|
|<span data-ttu-id="e6dee-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-352">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-353">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-353">String</span></span>|
|<span data-ttu-id="e6dee-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="e6dee-354">PRECISION</span></span>|<span data-ttu-id="e6dee-355">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-355">Int32</span></span>|
|<span data-ttu-id="e6dee-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e6dee-356">LENGTH</span></span>|<span data-ttu-id="e6dee-357">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-357">Int32</span></span>|
|<span data-ttu-id="e6dee-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="e6dee-358">SCALE</span></span>|<span data-ttu-id="e6dee-359">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-359">Int16</span></span>|
|<span data-ttu-id="e6dee-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-360">RADIX</span></span>|<span data-ttu-id="e6dee-361">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-361">Int16</span></span>|
|<span data-ttu-id="e6dee-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-362">NULLABLE</span></span>|<span data-ttu-id="e6dee-363">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-363">Int16</span></span>|
|<span data-ttu-id="e6dee-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-364">REMARKS</span></span>|<span data-ttu-id="e6dee-365">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-365">String</span></span>|
|<span data-ttu-id="e6dee-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-367">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="e6dee-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-368">Procedures</span></span>

|<span data-ttu-id="e6dee-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-369">ColumnName</span></span>|<span data-ttu-id="e6dee-370">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-372">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-372">String</span></span>|
|<span data-ttu-id="e6dee-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6dee-374">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-374">String</span></span>|
|<span data-ttu-id="e6dee-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-376">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-376">String</span></span>|
|<span data-ttu-id="e6dee-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-378">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-378">Int16</span></span>|
|<span data-ttu-id="e6dee-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-380">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-380">Int16</span></span>|
|<span data-ttu-id="e6dee-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6dee-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6dee-382">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-382">Int16</span></span>|
|<span data-ttu-id="e6dee-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-383">REMARKS</span></span>|<span data-ttu-id="e6dee-384">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-384">String</span></span>|
|<span data-ttu-id="e6dee-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6dee-386">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e6dee-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-387">ProcedureColumns</span></span>

|<span data-ttu-id="e6dee-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-388">ColumnName</span></span>|<span data-ttu-id="e6dee-389">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-391">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-391">String</span></span>|
|<span data-ttu-id="e6dee-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6dee-393">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-393">String</span></span>|
|<span data-ttu-id="e6dee-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-395">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-395">String</span></span>|
|<span data-ttu-id="e6dee-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-396">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-397">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-397">String</span></span>|
|<span data-ttu-id="e6dee-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-398">COLUMN_TYPE</span></span>|<span data-ttu-id="e6dee-399">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-399">Int16</span></span>|
|<span data-ttu-id="e6dee-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-400">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-401">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-401">Int16</span></span>|
|<span data-ttu-id="e6dee-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-402">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-403">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-403">String</span></span>|
|<span data-ttu-id="e6dee-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="e6dee-404">PRECISION</span></span>|<span data-ttu-id="e6dee-405">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-405">Int32</span></span>|
|<span data-ttu-id="e6dee-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e6dee-406">LENGTH</span></span>|<span data-ttu-id="e6dee-407">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-407">Int32</span></span>|
|<span data-ttu-id="e6dee-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="e6dee-408">SCALE</span></span>|<span data-ttu-id="e6dee-409">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-409">Int16</span></span>|
|<span data-ttu-id="e6dee-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-410">RADIX</span></span>|<span data-ttu-id="e6dee-411">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-411">Int16</span></span>|
|<span data-ttu-id="e6dee-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-412">NULLABLE</span></span>|<span data-ttu-id="e6dee-413">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-413">Int16</span></span>|
|<span data-ttu-id="e6dee-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-414">REMARKS</span></span>|<span data-ttu-id="e6dee-415">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-415">String</span></span>|
|<span data-ttu-id="e6dee-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="e6dee-416">OVERLOAD</span></span>|<span data-ttu-id="e6dee-417">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-417">Int32</span></span>|
|<span data-ttu-id="e6dee-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-419">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="e6dee-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="e6dee-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="e6dee-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="e6dee-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="e6dee-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="e6dee-422">Tables</span></span>

- <span data-ttu-id="e6dee-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="e6dee-423">Indexes</span></span>

- <span data-ttu-id="e6dee-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-424">Columns</span></span>

- <span data-ttu-id="e6dee-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-425">Procedures</span></span>

- <span data-ttu-id="e6dee-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-426">ProcedureColumns</span></span>

- <span data-ttu-id="e6dee-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6dee-427">ProcedureParameters</span></span>

- <span data-ttu-id="e6dee-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="e6dee-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="e6dee-429">Tables and Views</span></span>

|<span data-ttu-id="e6dee-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-430">ColumnName</span></span>|<span data-ttu-id="e6dee-431">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-433">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-433">String</span></span>|
|<span data-ttu-id="e6dee-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-434">TABLE_OWNER</span></span>|<span data-ttu-id="e6dee-435">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-435">String</span></span>|
|<span data-ttu-id="e6dee-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-436">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-437">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-437">String</span></span>|
|<span data-ttu-id="e6dee-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-438">TABLE_TYPE</span></span>|<span data-ttu-id="e6dee-439">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-439">String</span></span>|
|<span data-ttu-id="e6dee-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-440">REMARKS</span></span>|<span data-ttu-id="e6dee-441">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="e6dee-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-442">Columns</span></span>

|<span data-ttu-id="e6dee-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-443">ColumnName</span></span>|<span data-ttu-id="e6dee-444">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-446">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-446">String</span></span>|
|<span data-ttu-id="e6dee-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-447">TABLE_OWNER</span></span>|<span data-ttu-id="e6dee-448">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-448">String</span></span>|
|<span data-ttu-id="e6dee-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-449">TABLE_NAME</span></span>|<span data-ttu-id="e6dee-450">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-450">String</span></span>|
|<span data-ttu-id="e6dee-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-451">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-452">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-452">String</span></span>|
|<span data-ttu-id="e6dee-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-453">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-454">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-454">Int16</span></span>|
|<span data-ttu-id="e6dee-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-455">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-456">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-456">String</span></span>|
|<span data-ttu-id="e6dee-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="e6dee-457">PRECISION</span></span>|<span data-ttu-id="e6dee-458">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-458">Int32</span></span>|
|<span data-ttu-id="e6dee-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e6dee-459">LENGTH</span></span>|<span data-ttu-id="e6dee-460">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-460">Int32</span></span>|
|<span data-ttu-id="e6dee-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="e6dee-461">SCALE</span></span>|<span data-ttu-id="e6dee-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-462">Int16</span></span>|
|<span data-ttu-id="e6dee-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-463">RADIX</span></span>|<span data-ttu-id="e6dee-464">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-464">Int16</span></span>|
|<span data-ttu-id="e6dee-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-465">NULLABLE</span></span>|<span data-ttu-id="e6dee-466">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-466">Int16</span></span>|
|<span data-ttu-id="e6dee-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-467">REMARKS</span></span>|<span data-ttu-id="e6dee-468">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-468">String</span></span>|
|<span data-ttu-id="e6dee-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-470">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="e6dee-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6dee-471">Procedures</span></span>

|<span data-ttu-id="e6dee-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-472">ColumnName</span></span>|<span data-ttu-id="e6dee-473">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-475">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-475">String</span></span>|
|<span data-ttu-id="e6dee-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6dee-477">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-477">String</span></span>|
|<span data-ttu-id="e6dee-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-479">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-479">String</span></span>|
|<span data-ttu-id="e6dee-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-481">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-481">Int16</span></span>|
|<span data-ttu-id="e6dee-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="e6dee-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="e6dee-483">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-483">Int16</span></span>|
|<span data-ttu-id="e6dee-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="e6dee-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="e6dee-485">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-485">Int16</span></span>|
|<span data-ttu-id="e6dee-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-486">REMARKS</span></span>|<span data-ttu-id="e6dee-487">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-487">String</span></span>|
|<span data-ttu-id="e6dee-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e6dee-489">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="e6dee-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e6dee-490">ProcedureColumns</span></span>

|<span data-ttu-id="e6dee-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-491">ColumnName</span></span>|<span data-ttu-id="e6dee-492">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="e6dee-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="e6dee-494">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-494">String</span></span>|
|<span data-ttu-id="e6dee-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6dee-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="e6dee-496">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-496">String</span></span>|
|<span data-ttu-id="e6dee-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-498">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-498">String</span></span>|
|<span data-ttu-id="e6dee-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-499">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-500">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-500">String</span></span>|
|<span data-ttu-id="e6dee-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-501">COLUMN_TYPE</span></span>|<span data-ttu-id="e6dee-502">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-502">Int16</span></span>|
|<span data-ttu-id="e6dee-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-503">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-504">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-504">Int16</span></span>|
|<span data-ttu-id="e6dee-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-505">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-506">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-506">String</span></span>|
|<span data-ttu-id="e6dee-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="e6dee-507">PRECISION</span></span>|<span data-ttu-id="e6dee-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-508">Int32</span></span>|
|<span data-ttu-id="e6dee-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="e6dee-509">LENGTH</span></span>|<span data-ttu-id="e6dee-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-510">Int32</span></span>|
|<span data-ttu-id="e6dee-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="e6dee-511">SCALE</span></span>|<span data-ttu-id="e6dee-512">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-512">Int16</span></span>|
|<span data-ttu-id="e6dee-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-513">RADIX</span></span>|<span data-ttu-id="e6dee-514">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-514">Int16</span></span>|
|<span data-ttu-id="e6dee-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-515">NULLABLE</span></span>|<span data-ttu-id="e6dee-516">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-516">Int16</span></span>|
|<span data-ttu-id="e6dee-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-517">REMARKS</span></span>|<span data-ttu-id="e6dee-518">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-518">String</span></span>|
|<span data-ttu-id="e6dee-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="e6dee-519">OVERLOAD</span></span>|<span data-ttu-id="e6dee-520">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-520">Int32</span></span>|
|<span data-ttu-id="e6dee-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-522">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="e6dee-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e6dee-523">ProcedureParameters</span></span>

|<span data-ttu-id="e6dee-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="e6dee-524">ColumnName</span></span>|<span data-ttu-id="e6dee-525">DataType</span><span class="sxs-lookup"><span data-stu-id="e6dee-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="e6dee-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="e6dee-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="e6dee-527">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-527">String</span></span>|
|<span data-ttu-id="e6dee-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="e6dee-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="e6dee-529">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-529">String</span></span>|
|<span data-ttu-id="e6dee-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="e6dee-531">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-531">String</span></span>|
|<span data-ttu-id="e6dee-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-532">COLUMN_NAME</span></span>|<span data-ttu-id="e6dee-533">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-533">String</span></span>|
|<span data-ttu-id="e6dee-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-534">COLUMN_TYPE</span></span>|<span data-ttu-id="e6dee-535">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-535">Int16</span></span>|
|<span data-ttu-id="e6dee-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-536">DATA_TYPE</span></span>|<span data-ttu-id="e6dee-537">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-537">Int16</span></span>|
|<span data-ttu-id="e6dee-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e6dee-538">TYPE_NAME</span></span>|<span data-ttu-id="e6dee-539">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-539">String</span></span>|
|<span data-ttu-id="e6dee-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="e6dee-540">COLUMN_SIZE</span></span>|<span data-ttu-id="e6dee-541">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-541">Int32</span></span>|
|<span data-ttu-id="e6dee-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="e6dee-543">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-543">Int32</span></span>|
|<span data-ttu-id="e6dee-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="e6dee-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="e6dee-545">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-545">Int16</span></span>|
|<span data-ttu-id="e6dee-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="e6dee-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="e6dee-547">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-547">Int16</span></span>|
|<span data-ttu-id="e6dee-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-548">NULLABLE</span></span>|<span data-ttu-id="e6dee-549">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-549">Int16</span></span>|
|<span data-ttu-id="e6dee-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6dee-550">REMARKS</span></span>|<span data-ttu-id="e6dee-551">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-551">String</span></span>|
|<span data-ttu-id="e6dee-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="e6dee-552">COLUMN_DEF</span></span>|<span data-ttu-id="e6dee-553">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-553">String</span></span>|
|<span data-ttu-id="e6dee-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e6dee-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="e6dee-555">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-555">Int16</span></span>|
|<span data-ttu-id="e6dee-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="e6dee-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="e6dee-557">Int16</span><span class="sxs-lookup"><span data-stu-id="e6dee-557">Int16</span></span>|
|<span data-ttu-id="e6dee-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e6dee-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="e6dee-559">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-559">Int32</span></span>|
|<span data-ttu-id="e6dee-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e6dee-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="e6dee-561">Int32</span><span class="sxs-lookup"><span data-stu-id="e6dee-561">Int32</span></span>|
|<span data-ttu-id="e6dee-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e6dee-562">IS_NULLABLE</span></span>|<span data-ttu-id="e6dee-563">String</span><span class="sxs-lookup"><span data-stu-id="e6dee-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="e6dee-564">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6dee-564">See also</span></span>

- [<span data-ttu-id="e6dee-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e6dee-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
