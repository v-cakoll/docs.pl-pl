---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 36d0859b897bfcea33803c219ade14722ed90421
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="b7efb-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="b7efb-102">ODBC Schema Collections</span></span>
<span data-ttu-id="b7efb-103">W tej sekcji omówiono obsługi kolekcji schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="b7efb-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="b7efb-104">Sterownik ODBC programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="b7efb-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="b7efb-105">Sterownik ODBC programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b7efb-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b7efb-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="b7efb-106">Tables</span></span>  
  
-   <span data-ttu-id="b7efb-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b7efb-107">Indexes</span></span>  
  
-   <span data-ttu-id="b7efb-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-108">Columns</span></span>  
  
-   <span data-ttu-id="b7efb-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-109">Procedures</span></span>  
  
-   <span data-ttu-id="b7efb-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b7efb-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b7efb-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b7efb-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b7efb-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-113">Tables and Views</span></span>  
  
|<span data-ttu-id="b7efb-114">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-114">ColumnName</span></span>|<span data-ttu-id="b7efb-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-116">TABLE_CAT</span></span>|<span data-ttu-id="b7efb-117">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-117">String</span></span>|  
|<span data-ttu-id="b7efb-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-118">TABLE_SCHEM</span></span>|<span data-ttu-id="b7efb-119">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-119">String</span></span>|  
|<span data-ttu-id="b7efb-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-120">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-121">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-121">String</span></span>|  
|<span data-ttu-id="b7efb-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-122">TABLE_TYPE</span></span>|<span data-ttu-id="b7efb-123">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-123">String</span></span>|  
|<span data-ttu-id="b7efb-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-124">REMARKS</span></span>|<span data-ttu-id="b7efb-125">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b7efb-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b7efb-126">Indexes</span></span>  
  
|<span data-ttu-id="b7efb-127">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-127">ColumnName</span></span>|<span data-ttu-id="b7efb-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-129">TABLE_CAT</span></span>|<span data-ttu-id="b7efb-130">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-130">String</span></span>|  
|<span data-ttu-id="b7efb-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-131">TABLE_SCHEM</span></span>|<span data-ttu-id="b7efb-132">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-132">String</span></span>|  
|<span data-ttu-id="b7efb-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-133">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-134">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-134">String</span></span>|  
|<span data-ttu-id="b7efb-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b7efb-135">NON_UNIQUE</span></span>|<span data-ttu-id="b7efb-136">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-136">Int16</span></span>|  
|<span data-ttu-id="b7efb-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="b7efb-138">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-138">String</span></span>|  
|<span data-ttu-id="b7efb-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-139">INDEX_NAME</span></span>|<span data-ttu-id="b7efb-140">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-140">String</span></span>|  
|<span data-ttu-id="b7efb-141">TYP</span><span class="sxs-lookup"><span data-stu-id="b7efb-141">TYPE</span></span>|<span data-ttu-id="b7efb-142">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-142">Int16</span></span>|  
|<span data-ttu-id="b7efb-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-144">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-144">Int16</span></span>|  
|<span data-ttu-id="b7efb-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-145">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-146">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-146">String</span></span>|  
|<span data-ttu-id="b7efb-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="b7efb-147">ASC_OR_DESC</span></span>|<span data-ttu-id="b7efb-148">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-148">String</span></span>|  
|<span data-ttu-id="b7efb-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="b7efb-149">CARDINATLITY</span></span>|<span data-ttu-id="b7efb-150">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-150">Int32</span></span>|  
|<span data-ttu-id="b7efb-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="b7efb-151">PAGES</span></span>|<span data-ttu-id="b7efb-152">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-152">Int32</span></span>|  
|<span data-ttu-id="b7efb-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-153">FILTER_CONDITION</span></span>|<span data-ttu-id="b7efb-154">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-154">String</span></span>|  
|<span data-ttu-id="b7efb-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b7efb-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b7efb-156">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-156">String</span></span>|  
|<span data-ttu-id="b7efb-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-158">Byte</span><span class="sxs-lookup"><span data-stu-id="b7efb-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b7efb-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-159">Columns</span></span>  
  
|<span data-ttu-id="b7efb-160">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-160">ColumnName</span></span>|<span data-ttu-id="b7efb-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-162">TABLE_CAT</span></span>|<span data-ttu-id="b7efb-163">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-163">String</span></span>|  
|<span data-ttu-id="b7efb-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-164">TABLE_SCHEM</span></span>|<span data-ttu-id="b7efb-165">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-165">String</span></span>|  
|<span data-ttu-id="b7efb-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-166">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-167">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-167">String</span></span>|  
|<span data-ttu-id="b7efb-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-168">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-169">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-169">String</span></span>|  
|<span data-ttu-id="b7efb-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-170">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-171">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-171">Int16</span></span>|  
|<span data-ttu-id="b7efb-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-172">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-173">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-173">String</span></span>|  
|<span data-ttu-id="b7efb-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b7efb-174">COLUMN_SIZE</span></span>|<span data-ttu-id="b7efb-175">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-175">Int32</span></span>|  
|<span data-ttu-id="b7efb-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="b7efb-177">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-177">Int32</span></span>|  
|<span data-ttu-id="b7efb-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b7efb-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b7efb-179">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-179">Int16</span></span>|  
|<span data-ttu-id="b7efb-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b7efb-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b7efb-181">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-181">Int16</span></span>|  
|<span data-ttu-id="b7efb-182">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-182">NULLABLE</span></span>|<span data-ttu-id="b7efb-183">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-183">Int16</span></span>|  
|<span data-ttu-id="b7efb-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-184">REMARKS</span></span>|<span data-ttu-id="b7efb-185">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-185">String</span></span>|  
|<span data-ttu-id="b7efb-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b7efb-186">COLUMN_DEF</span></span>|<span data-ttu-id="b7efb-187">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-187">String</span></span>|  
|<span data-ttu-id="b7efb-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-189">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-189">Int16</span></span>|  
|<span data-ttu-id="b7efb-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b7efb-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b7efb-191">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-191">Int16</span></span>|  
|<span data-ttu-id="b7efb-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b7efb-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-193">Int32</span></span>|  
|<span data-ttu-id="b7efb-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-195">Int32</span></span>|  
|<span data-ttu-id="b7efb-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b7efb-196">IS_NULLABLE</span></span>|<span data-ttu-id="b7efb-197">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-197">String</span></span>|  
|<span data-ttu-id="b7efb-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b7efb-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b7efb-199">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-199">String</span></span>|  
|<span data-ttu-id="b7efb-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b7efb-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b7efb-201">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-201">String</span></span>|  
|<span data-ttu-id="b7efb-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-203">Byte</span><span class="sxs-lookup"><span data-stu-id="b7efb-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b7efb-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-204">Procedures</span></span>  
  
|<span data-ttu-id="b7efb-205">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-205">ColumnName</span></span>|<span data-ttu-id="b7efb-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="b7efb-208">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-208">String</span></span>|  
|<span data-ttu-id="b7efb-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b7efb-210">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-210">String</span></span>|  
|<span data-ttu-id="b7efb-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-212">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-212">String</span></span>|  
|<span data-ttu-id="b7efb-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-214">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-214">Int32</span></span>|  
|<span data-ttu-id="b7efb-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-216">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-216">Int32</span></span>|  
|<span data-ttu-id="b7efb-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b7efb-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b7efb-218">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-218">Int32</span></span>|  
|<span data-ttu-id="b7efb-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-219">REMARKS</span></span>|<span data-ttu-id="b7efb-220">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-220">String</span></span>|  
|<span data-ttu-id="b7efb-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b7efb-222">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b7efb-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b7efb-224">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-224">ColumnName</span></span>|<span data-ttu-id="b7efb-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="b7efb-227">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-227">String</span></span>|  
|<span data-ttu-id="b7efb-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b7efb-229">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-229">String</span></span>|  
|<span data-ttu-id="b7efb-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-231">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-231">String</span></span>|  
|<span data-ttu-id="b7efb-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-232">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-233">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-233">String</span></span>|  
|<span data-ttu-id="b7efb-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-234">COLUMN_TYPE</span></span>|<span data-ttu-id="b7efb-235">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-235">Int16</span></span>|  
|<span data-ttu-id="b7efb-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-236">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-237">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-237">Int16</span></span>|  
|<span data-ttu-id="b7efb-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-238">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-239">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-239">String</span></span>|  
|<span data-ttu-id="b7efb-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b7efb-240">COLUMN_SIZE</span></span>|<span data-ttu-id="b7efb-241">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-241">Int32</span></span>|  
|<span data-ttu-id="b7efb-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="b7efb-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-243">Int32</span></span>|  
|<span data-ttu-id="b7efb-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b7efb-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b7efb-245">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-245">Int16</span></span>|  
|<span data-ttu-id="b7efb-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b7efb-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b7efb-247">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-247">Int16</span></span>|  
|<span data-ttu-id="b7efb-248">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-248">NULLABLE</span></span>|<span data-ttu-id="b7efb-249">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-249">Int16</span></span>|  
|<span data-ttu-id="b7efb-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-250">REMARKS</span></span>|<span data-ttu-id="b7efb-251">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-251">String</span></span>|  
|<span data-ttu-id="b7efb-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b7efb-252">COLUMN_DEF</span></span>|<span data-ttu-id="b7efb-253">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-253">String</span></span>|  
|<span data-ttu-id="b7efb-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-255">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-255">Int16</span></span>|  
|<span data-ttu-id="b7efb-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b7efb-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b7efb-257">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-257">Int16</span></span>|  
|<span data-ttu-id="b7efb-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b7efb-259">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-259">Int32</span></span>|  
|<span data-ttu-id="b7efb-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-261">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-261">Int32</span></span>|  
|<span data-ttu-id="b7efb-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b7efb-262">IS_NULLABLE</span></span>|<span data-ttu-id="b7efb-263">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-263">String</span></span>|  
|<span data-ttu-id="b7efb-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b7efb-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b7efb-265">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-265">String</span></span>|  
|<span data-ttu-id="b7efb-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b7efb-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b7efb-267">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-267">String</span></span>|  
|<span data-ttu-id="b7efb-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-269">Byte</span><span class="sxs-lookup"><span data-stu-id="b7efb-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b7efb-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b7efb-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b7efb-271">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-271">ColumnName</span></span>|<span data-ttu-id="b7efb-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="b7efb-274">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-274">String</span></span>|  
|<span data-ttu-id="b7efb-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b7efb-276">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-276">String</span></span>|  
|<span data-ttu-id="b7efb-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-278">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-278">String</span></span>|  
|<span data-ttu-id="b7efb-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-279">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-280">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-280">String</span></span>|  
|<span data-ttu-id="b7efb-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-281">COLUMN_TYPE</span></span>|<span data-ttu-id="b7efb-282">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-282">Int16</span></span>|  
|<span data-ttu-id="b7efb-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-283">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-284">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-284">Int16</span></span>|  
|<span data-ttu-id="b7efb-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-285">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-286">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-286">String</span></span>|  
|<span data-ttu-id="b7efb-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b7efb-287">COLUMN_SIZE</span></span>|<span data-ttu-id="b7efb-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-288">Int32</span></span>|  
|<span data-ttu-id="b7efb-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="b7efb-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-290">Int32</span></span>|  
|<span data-ttu-id="b7efb-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b7efb-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b7efb-292">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-292">Int16</span></span>|  
|<span data-ttu-id="b7efb-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b7efb-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b7efb-294">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-294">Int16</span></span>|  
|<span data-ttu-id="b7efb-295">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-295">NULLABLE</span></span>|<span data-ttu-id="b7efb-296">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-296">Int16</span></span>|  
|<span data-ttu-id="b7efb-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-297">REMARKS</span></span>|<span data-ttu-id="b7efb-298">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-298">String</span></span>|  
|<span data-ttu-id="b7efb-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b7efb-299">COLUMN_DEF</span></span>|<span data-ttu-id="b7efb-300">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-300">String</span></span>|  
|<span data-ttu-id="b7efb-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-302">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-302">Int16</span></span>|  
|<span data-ttu-id="b7efb-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b7efb-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b7efb-304">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-304">Int16</span></span>|  
|<span data-ttu-id="b7efb-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b7efb-306">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-306">Int32</span></span>|  
|<span data-ttu-id="b7efb-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-308">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-308">Int32</span></span>|  
|<span data-ttu-id="b7efb-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b7efb-309">IS_NULLABLE</span></span>|<span data-ttu-id="b7efb-310">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-310">String</span></span>|  
|<span data-ttu-id="b7efb-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b7efb-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b7efb-312">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-312">String</span></span>|  
|<span data-ttu-id="b7efb-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b7efb-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b7efb-314">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-314">String</span></span>|  
|<span data-ttu-id="b7efb-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-316">Byte</span><span class="sxs-lookup"><span data-stu-id="b7efb-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="b7efb-317">Sterownik ODBC rozwiązań Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="b7efb-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="b7efb-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b7efb-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b7efb-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="b7efb-319">Tables</span></span>  
  
-   <span data-ttu-id="b7efb-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-320">Columns</span></span>  
  
-   <span data-ttu-id="b7efb-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-321">Procedures</span></span>  
  
-   <span data-ttu-id="b7efb-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b7efb-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b7efb-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b7efb-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-324">Views</span></span>  
  
-   <span data-ttu-id="b7efb-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b7efb-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b7efb-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-326">Tables and Views</span></span>  
  
|<span data-ttu-id="b7efb-327">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-327">ColumnName</span></span>|<span data-ttu-id="b7efb-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-330">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-330">String</span></span>|  
|<span data-ttu-id="b7efb-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-331">TABLE_OWNER</span></span>|<span data-ttu-id="b7efb-332">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-332">String</span></span>|  
|<span data-ttu-id="b7efb-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-333">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-334">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-334">String</span></span>|  
|<span data-ttu-id="b7efb-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-335">TABLE_TYPE</span></span>|<span data-ttu-id="b7efb-336">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-336">String</span></span>|  
|<span data-ttu-id="b7efb-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-337">REMARKS</span></span>|<span data-ttu-id="b7efb-338">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b7efb-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-339">Columns</span></span>  
  
|<span data-ttu-id="b7efb-340">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-340">ColumnName</span></span>|<span data-ttu-id="b7efb-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-343">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-343">String</span></span>|  
|<span data-ttu-id="b7efb-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-344">TABLE_OWNER</span></span>|<span data-ttu-id="b7efb-345">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-345">String</span></span>|  
|<span data-ttu-id="b7efb-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-346">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-347">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-347">String</span></span>|  
|<span data-ttu-id="b7efb-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-348">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-349">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-349">String</span></span>|  
|<span data-ttu-id="b7efb-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-350">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-351">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-351">Int16</span></span>|  
|<span data-ttu-id="b7efb-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-352">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-353">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-353">String</span></span>|  
|<span data-ttu-id="b7efb-354">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-354">PRECISION</span></span>|<span data-ttu-id="b7efb-355">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-355">Int32</span></span>|  
|<span data-ttu-id="b7efb-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-356">LENGTH</span></span>|<span data-ttu-id="b7efb-357">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-357">Int32</span></span>|  
|<span data-ttu-id="b7efb-358">SKALI</span><span class="sxs-lookup"><span data-stu-id="b7efb-358">SCALE</span></span>|<span data-ttu-id="b7efb-359">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-359">Int16</span></span>|  
|<span data-ttu-id="b7efb-360">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b7efb-360">RADIX</span></span>|<span data-ttu-id="b7efb-361">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-361">Int16</span></span>|  
|<span data-ttu-id="b7efb-362">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-362">NULLABLE</span></span>|<span data-ttu-id="b7efb-363">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-363">Int16</span></span>|  
|<span data-ttu-id="b7efb-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-364">REMARKS</span></span>|<span data-ttu-id="b7efb-365">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-365">String</span></span>|  
|<span data-ttu-id="b7efb-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-367">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b7efb-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-368">Procedures</span></span>  
  
|<span data-ttu-id="b7efb-369">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-369">ColumnName</span></span>|<span data-ttu-id="b7efb-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-372">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-372">String</span></span>|  
|<span data-ttu-id="b7efb-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b7efb-374">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-374">String</span></span>|  
|<span data-ttu-id="b7efb-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-376">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-376">String</span></span>|  
|<span data-ttu-id="b7efb-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-378">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-378">Int16</span></span>|  
|<span data-ttu-id="b7efb-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-380">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-380">Int16</span></span>|  
|<span data-ttu-id="b7efb-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b7efb-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b7efb-382">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-382">Int16</span></span>|  
|<span data-ttu-id="b7efb-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-383">REMARKS</span></span>|<span data-ttu-id="b7efb-384">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-384">String</span></span>|  
|<span data-ttu-id="b7efb-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b7efb-386">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b7efb-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b7efb-388">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-388">ColumnName</span></span>|<span data-ttu-id="b7efb-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-391">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-391">String</span></span>|  
|<span data-ttu-id="b7efb-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b7efb-393">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-393">String</span></span>|  
|<span data-ttu-id="b7efb-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-395">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-395">String</span></span>|  
|<span data-ttu-id="b7efb-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-396">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-397">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-397">String</span></span>|  
|<span data-ttu-id="b7efb-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-398">COLUMN_TYPE</span></span>|<span data-ttu-id="b7efb-399">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-399">Int16</span></span>|  
|<span data-ttu-id="b7efb-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-400">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-401">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-401">Int16</span></span>|  
|<span data-ttu-id="b7efb-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-402">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-403">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-403">String</span></span>|  
|<span data-ttu-id="b7efb-404">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-404">PRECISION</span></span>|<span data-ttu-id="b7efb-405">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-405">Int32</span></span>|  
|<span data-ttu-id="b7efb-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-406">LENGTH</span></span>|<span data-ttu-id="b7efb-407">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-407">Int32</span></span>|  
|<span data-ttu-id="b7efb-408">SKALI</span><span class="sxs-lookup"><span data-stu-id="b7efb-408">SCALE</span></span>|<span data-ttu-id="b7efb-409">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-409">Int16</span></span>|  
|<span data-ttu-id="b7efb-410">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b7efb-410">RADIX</span></span>|<span data-ttu-id="b7efb-411">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-411">Int16</span></span>|  
|<span data-ttu-id="b7efb-412">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-412">NULLABLE</span></span>|<span data-ttu-id="b7efb-413">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-413">Int16</span></span>|  
|<span data-ttu-id="b7efb-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-414">REMARKS</span></span>|<span data-ttu-id="b7efb-415">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-415">String</span></span>|  
|<span data-ttu-id="b7efb-416">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="b7efb-416">OVERLOAD</span></span>|<span data-ttu-id="b7efb-417">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-417">Int32</span></span>|  
|<span data-ttu-id="b7efb-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-419">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="b7efb-420">Sterownik ODBC dla programu Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="b7efb-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="b7efb-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b7efb-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b7efb-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="b7efb-422">Tables</span></span>  
  
-   <span data-ttu-id="b7efb-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b7efb-423">Indexes</span></span>  
  
-   <span data-ttu-id="b7efb-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-424">Columns</span></span>  
  
-   <span data-ttu-id="b7efb-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-425">Procedures</span></span>  
  
-   <span data-ttu-id="b7efb-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b7efb-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b7efb-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b7efb-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b7efb-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b7efb-429">Tables and Views</span></span>  
  
|<span data-ttu-id="b7efb-430">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-430">ColumnName</span></span>|<span data-ttu-id="b7efb-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-433">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-433">String</span></span>|  
|<span data-ttu-id="b7efb-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-434">TABLE_OWNER</span></span>|<span data-ttu-id="b7efb-435">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-435">String</span></span>|  
|<span data-ttu-id="b7efb-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-436">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-437">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-437">String</span></span>|  
|<span data-ttu-id="b7efb-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-438">TABLE_TYPE</span></span>|<span data-ttu-id="b7efb-439">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-439">String</span></span>|  
|<span data-ttu-id="b7efb-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-440">REMARKS</span></span>|<span data-ttu-id="b7efb-441">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b7efb-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b7efb-442">Columns</span></span>  
  
|<span data-ttu-id="b7efb-443">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-443">ColumnName</span></span>|<span data-ttu-id="b7efb-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-446">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-446">String</span></span>|  
|<span data-ttu-id="b7efb-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-447">TABLE_OWNER</span></span>|<span data-ttu-id="b7efb-448">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-448">String</span></span>|  
|<span data-ttu-id="b7efb-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-449">TABLE_NAME</span></span>|<span data-ttu-id="b7efb-450">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-450">String</span></span>|  
|<span data-ttu-id="b7efb-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-451">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-452">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-452">String</span></span>|  
|<span data-ttu-id="b7efb-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-453">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-454">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-454">Int16</span></span>|  
|<span data-ttu-id="b7efb-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-455">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-456">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-456">String</span></span>|  
|<span data-ttu-id="b7efb-457">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-457">PRECISION</span></span>|<span data-ttu-id="b7efb-458">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-458">Int32</span></span>|  
|<span data-ttu-id="b7efb-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-459">LENGTH</span></span>|<span data-ttu-id="b7efb-460">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-460">Int32</span></span>|  
|<span data-ttu-id="b7efb-461">SKALI</span><span class="sxs-lookup"><span data-stu-id="b7efb-461">SCALE</span></span>|<span data-ttu-id="b7efb-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-462">Int16</span></span>|  
|<span data-ttu-id="b7efb-463">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b7efb-463">RADIX</span></span>|<span data-ttu-id="b7efb-464">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-464">Int16</span></span>|  
|<span data-ttu-id="b7efb-465">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-465">NULLABLE</span></span>|<span data-ttu-id="b7efb-466">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-466">Int16</span></span>|  
|<span data-ttu-id="b7efb-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-467">REMARKS</span></span>|<span data-ttu-id="b7efb-468">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-468">String</span></span>|  
|<span data-ttu-id="b7efb-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-470">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b7efb-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="b7efb-471">Procedures</span></span>  
  
|<span data-ttu-id="b7efb-472">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-472">ColumnName</span></span>|<span data-ttu-id="b7efb-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-475">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-475">String</span></span>|  
|<span data-ttu-id="b7efb-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b7efb-477">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-477">String</span></span>|  
|<span data-ttu-id="b7efb-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-479">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-479">String</span></span>|  
|<span data-ttu-id="b7efb-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-481">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-481">Int16</span></span>|  
|<span data-ttu-id="b7efb-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b7efb-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b7efb-483">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-483">Int16</span></span>|  
|<span data-ttu-id="b7efb-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b7efb-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b7efb-485">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-485">Int16</span></span>|  
|<span data-ttu-id="b7efb-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-486">REMARKS</span></span>|<span data-ttu-id="b7efb-487">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-487">String</span></span>|  
|<span data-ttu-id="b7efb-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b7efb-489">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b7efb-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b7efb-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b7efb-491">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-491">ColumnName</span></span>|<span data-ttu-id="b7efb-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b7efb-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b7efb-494">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-494">String</span></span>|  
|<span data-ttu-id="b7efb-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7efb-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b7efb-496">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-496">String</span></span>|  
|<span data-ttu-id="b7efb-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-498">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-498">String</span></span>|  
|<span data-ttu-id="b7efb-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-499">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-500">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-500">String</span></span>|  
|<span data-ttu-id="b7efb-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-501">COLUMN_TYPE</span></span>|<span data-ttu-id="b7efb-502">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-502">Int16</span></span>|  
|<span data-ttu-id="b7efb-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-503">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-504">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-504">Int16</span></span>|  
|<span data-ttu-id="b7efb-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-505">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-506">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-506">String</span></span>|  
|<span data-ttu-id="b7efb-507">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-507">PRECISION</span></span>|<span data-ttu-id="b7efb-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-508">Int32</span></span>|  
|<span data-ttu-id="b7efb-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b7efb-509">LENGTH</span></span>|<span data-ttu-id="b7efb-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-510">Int32</span></span>|  
|<span data-ttu-id="b7efb-511">SKALI</span><span class="sxs-lookup"><span data-stu-id="b7efb-511">SCALE</span></span>|<span data-ttu-id="b7efb-512">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-512">Int16</span></span>|  
|<span data-ttu-id="b7efb-513">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b7efb-513">RADIX</span></span>|<span data-ttu-id="b7efb-514">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-514">Int16</span></span>|  
|<span data-ttu-id="b7efb-515">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-515">NULLABLE</span></span>|<span data-ttu-id="b7efb-516">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-516">Int16</span></span>|  
|<span data-ttu-id="b7efb-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-517">REMARKS</span></span>|<span data-ttu-id="b7efb-518">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-518">String</span></span>|  
|<span data-ttu-id="b7efb-519">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="b7efb-519">OVERLOAD</span></span>|<span data-ttu-id="b7efb-520">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-520">Int32</span></span>|  
|<span data-ttu-id="b7efb-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-522">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b7efb-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b7efb-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b7efb-524">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b7efb-524">ColumnName</span></span>|<span data-ttu-id="b7efb-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b7efb-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b7efb-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b7efb-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="b7efb-527">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-527">String</span></span>|  
|<span data-ttu-id="b7efb-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b7efb-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b7efb-529">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-529">String</span></span>|  
|<span data-ttu-id="b7efb-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="b7efb-531">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-531">String</span></span>|  
|<span data-ttu-id="b7efb-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-532">COLUMN_NAME</span></span>|<span data-ttu-id="b7efb-533">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-533">String</span></span>|  
|<span data-ttu-id="b7efb-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-534">COLUMN_TYPE</span></span>|<span data-ttu-id="b7efb-535">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-535">Int16</span></span>|  
|<span data-ttu-id="b7efb-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-536">DATA_TYPE</span></span>|<span data-ttu-id="b7efb-537">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-537">Int16</span></span>|  
|<span data-ttu-id="b7efb-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b7efb-538">TYPE_NAME</span></span>|<span data-ttu-id="b7efb-539">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-539">String</span></span>|  
|<span data-ttu-id="b7efb-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b7efb-540">COLUMN_SIZE</span></span>|<span data-ttu-id="b7efb-541">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-541">Int32</span></span>|  
|<span data-ttu-id="b7efb-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="b7efb-543">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-543">Int32</span></span>|  
|<span data-ttu-id="b7efb-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b7efb-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b7efb-545">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-545">Int16</span></span>|  
|<span data-ttu-id="b7efb-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b7efb-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b7efb-547">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-547">Int16</span></span>|  
|<span data-ttu-id="b7efb-548">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b7efb-548">NULLABLE</span></span>|<span data-ttu-id="b7efb-549">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-549">Int16</span></span>|  
|<span data-ttu-id="b7efb-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b7efb-550">REMARKS</span></span>|<span data-ttu-id="b7efb-551">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-551">String</span></span>|  
|<span data-ttu-id="b7efb-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b7efb-552">COLUMN_DEF</span></span>|<span data-ttu-id="b7efb-553">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-553">String</span></span>|  
|<span data-ttu-id="b7efb-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b7efb-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b7efb-555">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-555">Int16</span></span>|  
|<span data-ttu-id="b7efb-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b7efb-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b7efb-557">Int16</span><span class="sxs-lookup"><span data-stu-id="b7efb-557">Int16</span></span>|  
|<span data-ttu-id="b7efb-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b7efb-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b7efb-559">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-559">Int32</span></span>|  
|<span data-ttu-id="b7efb-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b7efb-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="b7efb-561">Int32</span><span class="sxs-lookup"><span data-stu-id="b7efb-561">Int32</span></span>|  
|<span data-ttu-id="b7efb-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b7efb-562">IS_NULLABLE</span></span>|<span data-ttu-id="b7efb-563">String</span><span class="sxs-lookup"><span data-stu-id="b7efb-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7efb-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7efb-564">See Also</span></span>  
 [<span data-ttu-id="b7efb-565">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b7efb-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
