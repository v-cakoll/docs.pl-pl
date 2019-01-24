---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 072a9cd365031cd5660d1824bc229d459abc5af8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525836"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="07929-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="07929-102">ODBC Schema Collections</span></span>
<span data-ttu-id="07929-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="07929-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="07929-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="07929-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="07929-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="07929-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="07929-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="07929-106">Tables</span></span>  
  
-   <span data-ttu-id="07929-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="07929-107">Indexes</span></span>  
  
-   <span data-ttu-id="07929-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-108">Columns</span></span>  
  
-   <span data-ttu-id="07929-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-109">Procedures</span></span>  
  
-   <span data-ttu-id="07929-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="07929-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07929-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="07929-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="07929-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="07929-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="07929-113">Tables and Views</span></span>  
  
|<span data-ttu-id="07929-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-114">ColumnName</span></span>|<span data-ttu-id="07929-115">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-116">TABLE_CAT</span></span>|<span data-ttu-id="07929-117">String</span><span class="sxs-lookup"><span data-stu-id="07929-117">String</span></span>|  
|<span data-ttu-id="07929-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-118">TABLE_SCHEM</span></span>|<span data-ttu-id="07929-119">String</span><span class="sxs-lookup"><span data-stu-id="07929-119">String</span></span>|  
|<span data-ttu-id="07929-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-120">TABLE_NAME</span></span>|<span data-ttu-id="07929-121">String</span><span class="sxs-lookup"><span data-stu-id="07929-121">String</span></span>|  
|<span data-ttu-id="07929-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-122">TABLE_TYPE</span></span>|<span data-ttu-id="07929-123">String</span><span class="sxs-lookup"><span data-stu-id="07929-123">String</span></span>|  
|<span data-ttu-id="07929-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-124">REMARKS</span></span>|<span data-ttu-id="07929-125">String</span><span class="sxs-lookup"><span data-stu-id="07929-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="07929-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="07929-126">Indexes</span></span>  
  
|<span data-ttu-id="07929-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-127">ColumnName</span></span>|<span data-ttu-id="07929-128">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-129">TABLE_CAT</span></span>|<span data-ttu-id="07929-130">String</span><span class="sxs-lookup"><span data-stu-id="07929-130">String</span></span>|  
|<span data-ttu-id="07929-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-131">TABLE_SCHEM</span></span>|<span data-ttu-id="07929-132">String</span><span class="sxs-lookup"><span data-stu-id="07929-132">String</span></span>|  
|<span data-ttu-id="07929-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-133">TABLE_NAME</span></span>|<span data-ttu-id="07929-134">String</span><span class="sxs-lookup"><span data-stu-id="07929-134">String</span></span>|  
|<span data-ttu-id="07929-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="07929-135">NON_UNIQUE</span></span>|<span data-ttu-id="07929-136">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-136">Int16</span></span>|  
|<span data-ttu-id="07929-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="07929-138">String</span><span class="sxs-lookup"><span data-stu-id="07929-138">String</span></span>|  
|<span data-ttu-id="07929-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-139">INDEX_NAME</span></span>|<span data-ttu-id="07929-140">String</span><span class="sxs-lookup"><span data-stu-id="07929-140">String</span></span>|  
|<span data-ttu-id="07929-141">TYP</span><span class="sxs-lookup"><span data-stu-id="07929-141">TYPE</span></span>|<span data-ttu-id="07929-142">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-142">Int16</span></span>|  
|<span data-ttu-id="07929-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-144">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-144">Int16</span></span>|  
|<span data-ttu-id="07929-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-145">COLUMN_NAME</span></span>|<span data-ttu-id="07929-146">String</span><span class="sxs-lookup"><span data-stu-id="07929-146">String</span></span>|  
|<span data-ttu-id="07929-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="07929-147">ASC_OR_DESC</span></span>|<span data-ttu-id="07929-148">String</span><span class="sxs-lookup"><span data-stu-id="07929-148">String</span></span>|  
|<span data-ttu-id="07929-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="07929-149">CARDINATLITY</span></span>|<span data-ttu-id="07929-150">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-150">Int32</span></span>|  
|<span data-ttu-id="07929-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="07929-151">PAGES</span></span>|<span data-ttu-id="07929-152">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-152">Int32</span></span>|  
|<span data-ttu-id="07929-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="07929-153">FILTER_CONDITION</span></span>|<span data-ttu-id="07929-154">String</span><span class="sxs-lookup"><span data-stu-id="07929-154">String</span></span>|  
|<span data-ttu-id="07929-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07929-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="07929-156">String</span><span class="sxs-lookup"><span data-stu-id="07929-156">String</span></span>|  
|<span data-ttu-id="07929-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="07929-158">Byte</span><span class="sxs-lookup"><span data-stu-id="07929-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="07929-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-159">Columns</span></span>  
  
|<span data-ttu-id="07929-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-160">ColumnName</span></span>|<span data-ttu-id="07929-161">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-162">TABLE_CAT</span></span>|<span data-ttu-id="07929-163">String</span><span class="sxs-lookup"><span data-stu-id="07929-163">String</span></span>|  
|<span data-ttu-id="07929-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-164">TABLE_SCHEM</span></span>|<span data-ttu-id="07929-165">String</span><span class="sxs-lookup"><span data-stu-id="07929-165">String</span></span>|  
|<span data-ttu-id="07929-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-166">TABLE_NAME</span></span>|<span data-ttu-id="07929-167">String</span><span class="sxs-lookup"><span data-stu-id="07929-167">String</span></span>|  
|<span data-ttu-id="07929-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-168">COLUMN_NAME</span></span>|<span data-ttu-id="07929-169">String</span><span class="sxs-lookup"><span data-stu-id="07929-169">String</span></span>|  
|<span data-ttu-id="07929-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-170">DATA_TYPE</span></span>|<span data-ttu-id="07929-171">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-171">Int16</span></span>|  
|<span data-ttu-id="07929-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-172">TYPE_NAME</span></span>|<span data-ttu-id="07929-173">String</span><span class="sxs-lookup"><span data-stu-id="07929-173">String</span></span>|  
|<span data-ttu-id="07929-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="07929-174">COLUMN_SIZE</span></span>|<span data-ttu-id="07929-175">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-175">Int32</span></span>|  
|<span data-ttu-id="07929-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="07929-177">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-177">Int32</span></span>|  
|<span data-ttu-id="07929-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="07929-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="07929-179">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-179">Int16</span></span>|  
|<span data-ttu-id="07929-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="07929-181">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-181">Int16</span></span>|  
|<span data-ttu-id="07929-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-182">NULLABLE</span></span>|<span data-ttu-id="07929-183">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-183">Int16</span></span>|  
|<span data-ttu-id="07929-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-184">REMARKS</span></span>|<span data-ttu-id="07929-185">String</span><span class="sxs-lookup"><span data-stu-id="07929-185">String</span></span>|  
|<span data-ttu-id="07929-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="07929-186">COLUMN_DEF</span></span>|<span data-ttu-id="07929-187">String</span><span class="sxs-lookup"><span data-stu-id="07929-187">String</span></span>|  
|<span data-ttu-id="07929-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="07929-189">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-189">Int16</span></span>|  
|<span data-ttu-id="07929-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="07929-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="07929-191">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-191">Int16</span></span>|  
|<span data-ttu-id="07929-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="07929-193">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-193">Int32</span></span>|  
|<span data-ttu-id="07929-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-195">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-195">Int32</span></span>|  
|<span data-ttu-id="07929-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-196">IS_NULLABLE</span></span>|<span data-ttu-id="07929-197">String</span><span class="sxs-lookup"><span data-stu-id="07929-197">String</span></span>|  
|<span data-ttu-id="07929-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07929-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="07929-199">String</span><span class="sxs-lookup"><span data-stu-id="07929-199">String</span></span>|  
|<span data-ttu-id="07929-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07929-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="07929-201">String</span><span class="sxs-lookup"><span data-stu-id="07929-201">String</span></span>|  
|<span data-ttu-id="07929-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="07929-203">Byte</span><span class="sxs-lookup"><span data-stu-id="07929-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="07929-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-204">Procedures</span></span>  
  
|<span data-ttu-id="07929-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-205">ColumnName</span></span>|<span data-ttu-id="07929-206">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="07929-208">String</span><span class="sxs-lookup"><span data-stu-id="07929-208">String</span></span>|  
|<span data-ttu-id="07929-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="07929-210">String</span><span class="sxs-lookup"><span data-stu-id="07929-210">String</span></span>|  
|<span data-ttu-id="07929-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-212">String</span><span class="sxs-lookup"><span data-stu-id="07929-212">String</span></span>|  
|<span data-ttu-id="07929-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="07929-214">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-214">Int32</span></span>|  
|<span data-ttu-id="07929-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="07929-216">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-216">Int32</span></span>|  
|<span data-ttu-id="07929-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="07929-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="07929-218">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-218">Int32</span></span>|  
|<span data-ttu-id="07929-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-219">REMARKS</span></span>|<span data-ttu-id="07929-220">String</span><span class="sxs-lookup"><span data-stu-id="07929-220">String</span></span>|  
|<span data-ttu-id="07929-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="07929-222">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="07929-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="07929-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-224">ColumnName</span></span>|<span data-ttu-id="07929-225">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="07929-227">String</span><span class="sxs-lookup"><span data-stu-id="07929-227">String</span></span>|  
|<span data-ttu-id="07929-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="07929-229">String</span><span class="sxs-lookup"><span data-stu-id="07929-229">String</span></span>|  
|<span data-ttu-id="07929-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-231">String</span><span class="sxs-lookup"><span data-stu-id="07929-231">String</span></span>|  
|<span data-ttu-id="07929-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-232">COLUMN_NAME</span></span>|<span data-ttu-id="07929-233">String</span><span class="sxs-lookup"><span data-stu-id="07929-233">String</span></span>|  
|<span data-ttu-id="07929-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-234">COLUMN_TYPE</span></span>|<span data-ttu-id="07929-235">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-235">Int16</span></span>|  
|<span data-ttu-id="07929-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-236">DATA_TYPE</span></span>|<span data-ttu-id="07929-237">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-237">Int16</span></span>|  
|<span data-ttu-id="07929-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-238">TYPE_NAME</span></span>|<span data-ttu-id="07929-239">String</span><span class="sxs-lookup"><span data-stu-id="07929-239">String</span></span>|  
|<span data-ttu-id="07929-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="07929-240">COLUMN_SIZE</span></span>|<span data-ttu-id="07929-241">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-241">Int32</span></span>|  
|<span data-ttu-id="07929-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="07929-243">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-243">Int32</span></span>|  
|<span data-ttu-id="07929-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="07929-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="07929-245">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-245">Int16</span></span>|  
|<span data-ttu-id="07929-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="07929-247">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-247">Int16</span></span>|  
|<span data-ttu-id="07929-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-248">NULLABLE</span></span>|<span data-ttu-id="07929-249">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-249">Int16</span></span>|  
|<span data-ttu-id="07929-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-250">REMARKS</span></span>|<span data-ttu-id="07929-251">String</span><span class="sxs-lookup"><span data-stu-id="07929-251">String</span></span>|  
|<span data-ttu-id="07929-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="07929-252">COLUMN_DEF</span></span>|<span data-ttu-id="07929-253">String</span><span class="sxs-lookup"><span data-stu-id="07929-253">String</span></span>|  
|<span data-ttu-id="07929-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="07929-255">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-255">Int16</span></span>|  
|<span data-ttu-id="07929-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="07929-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="07929-257">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-257">Int16</span></span>|  
|<span data-ttu-id="07929-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="07929-259">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-259">Int32</span></span>|  
|<span data-ttu-id="07929-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-261">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-261">Int32</span></span>|  
|<span data-ttu-id="07929-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-262">IS_NULLABLE</span></span>|<span data-ttu-id="07929-263">String</span><span class="sxs-lookup"><span data-stu-id="07929-263">String</span></span>|  
|<span data-ttu-id="07929-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07929-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="07929-265">String</span><span class="sxs-lookup"><span data-stu-id="07929-265">String</span></span>|  
|<span data-ttu-id="07929-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07929-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="07929-267">String</span><span class="sxs-lookup"><span data-stu-id="07929-267">String</span></span>|  
|<span data-ttu-id="07929-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="07929-269">Byte</span><span class="sxs-lookup"><span data-stu-id="07929-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="07929-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07929-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="07929-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-271">ColumnName</span></span>|<span data-ttu-id="07929-272">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="07929-274">String</span><span class="sxs-lookup"><span data-stu-id="07929-274">String</span></span>|  
|<span data-ttu-id="07929-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="07929-276">String</span><span class="sxs-lookup"><span data-stu-id="07929-276">String</span></span>|  
|<span data-ttu-id="07929-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-278">String</span><span class="sxs-lookup"><span data-stu-id="07929-278">String</span></span>|  
|<span data-ttu-id="07929-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-279">COLUMN_NAME</span></span>|<span data-ttu-id="07929-280">String</span><span class="sxs-lookup"><span data-stu-id="07929-280">String</span></span>|  
|<span data-ttu-id="07929-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-281">COLUMN_TYPE</span></span>|<span data-ttu-id="07929-282">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-282">Int16</span></span>|  
|<span data-ttu-id="07929-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-283">DATA_TYPE</span></span>|<span data-ttu-id="07929-284">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-284">Int16</span></span>|  
|<span data-ttu-id="07929-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-285">TYPE_NAME</span></span>|<span data-ttu-id="07929-286">String</span><span class="sxs-lookup"><span data-stu-id="07929-286">String</span></span>|  
|<span data-ttu-id="07929-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="07929-287">COLUMN_SIZE</span></span>|<span data-ttu-id="07929-288">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-288">Int32</span></span>|  
|<span data-ttu-id="07929-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="07929-290">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-290">Int32</span></span>|  
|<span data-ttu-id="07929-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="07929-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="07929-292">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-292">Int16</span></span>|  
|<span data-ttu-id="07929-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="07929-294">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-294">Int16</span></span>|  
|<span data-ttu-id="07929-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-295">NULLABLE</span></span>|<span data-ttu-id="07929-296">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-296">Int16</span></span>|  
|<span data-ttu-id="07929-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-297">REMARKS</span></span>|<span data-ttu-id="07929-298">String</span><span class="sxs-lookup"><span data-stu-id="07929-298">String</span></span>|  
|<span data-ttu-id="07929-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="07929-299">COLUMN_DEF</span></span>|<span data-ttu-id="07929-300">String</span><span class="sxs-lookup"><span data-stu-id="07929-300">String</span></span>|  
|<span data-ttu-id="07929-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="07929-302">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-302">Int16</span></span>|  
|<span data-ttu-id="07929-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="07929-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="07929-304">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-304">Int16</span></span>|  
|<span data-ttu-id="07929-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="07929-306">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-306">Int32</span></span>|  
|<span data-ttu-id="07929-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-308">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-308">Int32</span></span>|  
|<span data-ttu-id="07929-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-309">IS_NULLABLE</span></span>|<span data-ttu-id="07929-310">String</span><span class="sxs-lookup"><span data-stu-id="07929-310">String</span></span>|  
|<span data-ttu-id="07929-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07929-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="07929-312">String</span><span class="sxs-lookup"><span data-stu-id="07929-312">String</span></span>|  
|<span data-ttu-id="07929-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07929-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="07929-314">String</span><span class="sxs-lookup"><span data-stu-id="07929-314">String</span></span>|  
|<span data-ttu-id="07929-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="07929-316">Byte</span><span class="sxs-lookup"><span data-stu-id="07929-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="07929-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="07929-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="07929-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="07929-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="07929-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="07929-319">Tables</span></span>  
  
-   <span data-ttu-id="07929-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-320">Columns</span></span>  
  
-   <span data-ttu-id="07929-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-321">Procedures</span></span>  
  
-   <span data-ttu-id="07929-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="07929-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07929-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="07929-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="07929-324">Views</span></span>  
  
-   <span data-ttu-id="07929-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="07929-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="07929-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="07929-326">Tables and Views</span></span>  
  
|<span data-ttu-id="07929-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-327">ColumnName</span></span>|<span data-ttu-id="07929-328">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="07929-330">String</span><span class="sxs-lookup"><span data-stu-id="07929-330">String</span></span>|  
|<span data-ttu-id="07929-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-331">TABLE_OWNER</span></span>|<span data-ttu-id="07929-332">String</span><span class="sxs-lookup"><span data-stu-id="07929-332">String</span></span>|  
|<span data-ttu-id="07929-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-333">TABLE_NAME</span></span>|<span data-ttu-id="07929-334">String</span><span class="sxs-lookup"><span data-stu-id="07929-334">String</span></span>|  
|<span data-ttu-id="07929-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-335">TABLE_TYPE</span></span>|<span data-ttu-id="07929-336">String</span><span class="sxs-lookup"><span data-stu-id="07929-336">String</span></span>|  
|<span data-ttu-id="07929-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-337">REMARKS</span></span>|<span data-ttu-id="07929-338">String</span><span class="sxs-lookup"><span data-stu-id="07929-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="07929-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-339">Columns</span></span>  
  
|<span data-ttu-id="07929-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-340">ColumnName</span></span>|<span data-ttu-id="07929-341">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="07929-343">String</span><span class="sxs-lookup"><span data-stu-id="07929-343">String</span></span>|  
|<span data-ttu-id="07929-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-344">TABLE_OWNER</span></span>|<span data-ttu-id="07929-345">String</span><span class="sxs-lookup"><span data-stu-id="07929-345">String</span></span>|  
|<span data-ttu-id="07929-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-346">TABLE_NAME</span></span>|<span data-ttu-id="07929-347">String</span><span class="sxs-lookup"><span data-stu-id="07929-347">String</span></span>|  
|<span data-ttu-id="07929-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-348">COLUMN_NAME</span></span>|<span data-ttu-id="07929-349">String</span><span class="sxs-lookup"><span data-stu-id="07929-349">String</span></span>|  
|<span data-ttu-id="07929-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-350">DATA_TYPE</span></span>|<span data-ttu-id="07929-351">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-351">Int16</span></span>|  
|<span data-ttu-id="07929-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-352">TYPE_NAME</span></span>|<span data-ttu-id="07929-353">String</span><span class="sxs-lookup"><span data-stu-id="07929-353">String</span></span>|  
|<span data-ttu-id="07929-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="07929-354">PRECISION</span></span>|<span data-ttu-id="07929-355">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-355">Int32</span></span>|  
|<span data-ttu-id="07929-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="07929-356">LENGTH</span></span>|<span data-ttu-id="07929-357">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-357">Int32</span></span>|  
|<span data-ttu-id="07929-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="07929-358">SCALE</span></span>|<span data-ttu-id="07929-359">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-359">Int16</span></span>|  
|<span data-ttu-id="07929-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-360">RADIX</span></span>|<span data-ttu-id="07929-361">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-361">Int16</span></span>|  
|<span data-ttu-id="07929-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-362">NULLABLE</span></span>|<span data-ttu-id="07929-363">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-363">Int16</span></span>|  
|<span data-ttu-id="07929-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-364">REMARKS</span></span>|<span data-ttu-id="07929-365">String</span><span class="sxs-lookup"><span data-stu-id="07929-365">String</span></span>|  
|<span data-ttu-id="07929-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-367">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="07929-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-368">Procedures</span></span>  
  
|<span data-ttu-id="07929-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-369">ColumnName</span></span>|<span data-ttu-id="07929-370">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="07929-372">String</span><span class="sxs-lookup"><span data-stu-id="07929-372">String</span></span>|  
|<span data-ttu-id="07929-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="07929-374">String</span><span class="sxs-lookup"><span data-stu-id="07929-374">String</span></span>|  
|<span data-ttu-id="07929-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-376">String</span><span class="sxs-lookup"><span data-stu-id="07929-376">String</span></span>|  
|<span data-ttu-id="07929-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="07929-378">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-378">Int16</span></span>|  
|<span data-ttu-id="07929-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="07929-380">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-380">Int16</span></span>|  
|<span data-ttu-id="07929-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="07929-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="07929-382">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-382">Int16</span></span>|  
|<span data-ttu-id="07929-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-383">REMARKS</span></span>|<span data-ttu-id="07929-384">String</span><span class="sxs-lookup"><span data-stu-id="07929-384">String</span></span>|  
|<span data-ttu-id="07929-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="07929-386">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="07929-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="07929-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-388">ColumnName</span></span>|<span data-ttu-id="07929-389">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="07929-391">String</span><span class="sxs-lookup"><span data-stu-id="07929-391">String</span></span>|  
|<span data-ttu-id="07929-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="07929-393">String</span><span class="sxs-lookup"><span data-stu-id="07929-393">String</span></span>|  
|<span data-ttu-id="07929-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-395">String</span><span class="sxs-lookup"><span data-stu-id="07929-395">String</span></span>|  
|<span data-ttu-id="07929-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-396">COLUMN_NAME</span></span>|<span data-ttu-id="07929-397">String</span><span class="sxs-lookup"><span data-stu-id="07929-397">String</span></span>|  
|<span data-ttu-id="07929-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-398">COLUMN_TYPE</span></span>|<span data-ttu-id="07929-399">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-399">Int16</span></span>|  
|<span data-ttu-id="07929-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-400">DATA_TYPE</span></span>|<span data-ttu-id="07929-401">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-401">Int16</span></span>|  
|<span data-ttu-id="07929-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-402">TYPE_NAME</span></span>|<span data-ttu-id="07929-403">String</span><span class="sxs-lookup"><span data-stu-id="07929-403">String</span></span>|  
|<span data-ttu-id="07929-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="07929-404">PRECISION</span></span>|<span data-ttu-id="07929-405">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-405">Int32</span></span>|  
|<span data-ttu-id="07929-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="07929-406">LENGTH</span></span>|<span data-ttu-id="07929-407">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-407">Int32</span></span>|  
|<span data-ttu-id="07929-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="07929-408">SCALE</span></span>|<span data-ttu-id="07929-409">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-409">Int16</span></span>|  
|<span data-ttu-id="07929-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-410">RADIX</span></span>|<span data-ttu-id="07929-411">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-411">Int16</span></span>|  
|<span data-ttu-id="07929-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-412">NULLABLE</span></span>|<span data-ttu-id="07929-413">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-413">Int16</span></span>|  
|<span data-ttu-id="07929-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-414">REMARKS</span></span>|<span data-ttu-id="07929-415">String</span><span class="sxs-lookup"><span data-stu-id="07929-415">String</span></span>|  
|<span data-ttu-id="07929-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="07929-416">OVERLOAD</span></span>|<span data-ttu-id="07929-417">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-417">Int32</span></span>|  
|<span data-ttu-id="07929-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-419">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="07929-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="07929-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="07929-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="07929-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="07929-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="07929-422">Tables</span></span>  
  
-   <span data-ttu-id="07929-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="07929-423">Indexes</span></span>  
  
-   <span data-ttu-id="07929-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-424">Columns</span></span>  
  
-   <span data-ttu-id="07929-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-425">Procedures</span></span>  
  
-   <span data-ttu-id="07929-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="07929-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07929-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="07929-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="07929-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="07929-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="07929-429">Tables and Views</span></span>  
  
|<span data-ttu-id="07929-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-430">ColumnName</span></span>|<span data-ttu-id="07929-431">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="07929-433">String</span><span class="sxs-lookup"><span data-stu-id="07929-433">String</span></span>|  
|<span data-ttu-id="07929-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-434">TABLE_OWNER</span></span>|<span data-ttu-id="07929-435">String</span><span class="sxs-lookup"><span data-stu-id="07929-435">String</span></span>|  
|<span data-ttu-id="07929-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-436">TABLE_NAME</span></span>|<span data-ttu-id="07929-437">String</span><span class="sxs-lookup"><span data-stu-id="07929-437">String</span></span>|  
|<span data-ttu-id="07929-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-438">TABLE_TYPE</span></span>|<span data-ttu-id="07929-439">String</span><span class="sxs-lookup"><span data-stu-id="07929-439">String</span></span>|  
|<span data-ttu-id="07929-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-440">REMARKS</span></span>|<span data-ttu-id="07929-441">String</span><span class="sxs-lookup"><span data-stu-id="07929-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="07929-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07929-442">Columns</span></span>  
  
|<span data-ttu-id="07929-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-443">ColumnName</span></span>|<span data-ttu-id="07929-444">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="07929-446">String</span><span class="sxs-lookup"><span data-stu-id="07929-446">String</span></span>|  
|<span data-ttu-id="07929-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-447">TABLE_OWNER</span></span>|<span data-ttu-id="07929-448">String</span><span class="sxs-lookup"><span data-stu-id="07929-448">String</span></span>|  
|<span data-ttu-id="07929-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-449">TABLE_NAME</span></span>|<span data-ttu-id="07929-450">String</span><span class="sxs-lookup"><span data-stu-id="07929-450">String</span></span>|  
|<span data-ttu-id="07929-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-451">COLUMN_NAME</span></span>|<span data-ttu-id="07929-452">String</span><span class="sxs-lookup"><span data-stu-id="07929-452">String</span></span>|  
|<span data-ttu-id="07929-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-453">DATA_TYPE</span></span>|<span data-ttu-id="07929-454">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-454">Int16</span></span>|  
|<span data-ttu-id="07929-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-455">TYPE_NAME</span></span>|<span data-ttu-id="07929-456">String</span><span class="sxs-lookup"><span data-stu-id="07929-456">String</span></span>|  
|<span data-ttu-id="07929-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="07929-457">PRECISION</span></span>|<span data-ttu-id="07929-458">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-458">Int32</span></span>|  
|<span data-ttu-id="07929-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="07929-459">LENGTH</span></span>|<span data-ttu-id="07929-460">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-460">Int32</span></span>|  
|<span data-ttu-id="07929-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="07929-461">SCALE</span></span>|<span data-ttu-id="07929-462">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-462">Int16</span></span>|  
|<span data-ttu-id="07929-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-463">RADIX</span></span>|<span data-ttu-id="07929-464">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-464">Int16</span></span>|  
|<span data-ttu-id="07929-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-465">NULLABLE</span></span>|<span data-ttu-id="07929-466">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-466">Int16</span></span>|  
|<span data-ttu-id="07929-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-467">REMARKS</span></span>|<span data-ttu-id="07929-468">String</span><span class="sxs-lookup"><span data-stu-id="07929-468">String</span></span>|  
|<span data-ttu-id="07929-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-470">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="07929-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="07929-471">Procedures</span></span>  
  
|<span data-ttu-id="07929-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-472">ColumnName</span></span>|<span data-ttu-id="07929-473">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="07929-475">String</span><span class="sxs-lookup"><span data-stu-id="07929-475">String</span></span>|  
|<span data-ttu-id="07929-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="07929-477">String</span><span class="sxs-lookup"><span data-stu-id="07929-477">String</span></span>|  
|<span data-ttu-id="07929-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-479">String</span><span class="sxs-lookup"><span data-stu-id="07929-479">String</span></span>|  
|<span data-ttu-id="07929-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="07929-481">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-481">Int16</span></span>|  
|<span data-ttu-id="07929-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="07929-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="07929-483">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-483">Int16</span></span>|  
|<span data-ttu-id="07929-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="07929-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="07929-485">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-485">Int16</span></span>|  
|<span data-ttu-id="07929-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-486">REMARKS</span></span>|<span data-ttu-id="07929-487">String</span><span class="sxs-lookup"><span data-stu-id="07929-487">String</span></span>|  
|<span data-ttu-id="07929-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="07929-489">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="07929-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="07929-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="07929-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-491">ColumnName</span></span>|<span data-ttu-id="07929-492">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="07929-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="07929-494">String</span><span class="sxs-lookup"><span data-stu-id="07929-494">String</span></span>|  
|<span data-ttu-id="07929-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="07929-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="07929-496">String</span><span class="sxs-lookup"><span data-stu-id="07929-496">String</span></span>|  
|<span data-ttu-id="07929-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-498">String</span><span class="sxs-lookup"><span data-stu-id="07929-498">String</span></span>|  
|<span data-ttu-id="07929-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-499">COLUMN_NAME</span></span>|<span data-ttu-id="07929-500">String</span><span class="sxs-lookup"><span data-stu-id="07929-500">String</span></span>|  
|<span data-ttu-id="07929-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-501">COLUMN_TYPE</span></span>|<span data-ttu-id="07929-502">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-502">Int16</span></span>|  
|<span data-ttu-id="07929-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-503">DATA_TYPE</span></span>|<span data-ttu-id="07929-504">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-504">Int16</span></span>|  
|<span data-ttu-id="07929-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-505">TYPE_NAME</span></span>|<span data-ttu-id="07929-506">String</span><span class="sxs-lookup"><span data-stu-id="07929-506">String</span></span>|  
|<span data-ttu-id="07929-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="07929-507">PRECISION</span></span>|<span data-ttu-id="07929-508">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-508">Int32</span></span>|  
|<span data-ttu-id="07929-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="07929-509">LENGTH</span></span>|<span data-ttu-id="07929-510">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-510">Int32</span></span>|  
|<span data-ttu-id="07929-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="07929-511">SCALE</span></span>|<span data-ttu-id="07929-512">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-512">Int16</span></span>|  
|<span data-ttu-id="07929-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-513">RADIX</span></span>|<span data-ttu-id="07929-514">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-514">Int16</span></span>|  
|<span data-ttu-id="07929-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-515">NULLABLE</span></span>|<span data-ttu-id="07929-516">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-516">Int16</span></span>|  
|<span data-ttu-id="07929-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-517">REMARKS</span></span>|<span data-ttu-id="07929-518">String</span><span class="sxs-lookup"><span data-stu-id="07929-518">String</span></span>|  
|<span data-ttu-id="07929-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="07929-519">OVERLOAD</span></span>|<span data-ttu-id="07929-520">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-520">Int32</span></span>|  
|<span data-ttu-id="07929-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-522">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="07929-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="07929-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="07929-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="07929-524">ColumnName</span></span>|<span data-ttu-id="07929-525">DataType</span><span class="sxs-lookup"><span data-stu-id="07929-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="07929-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="07929-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="07929-527">String</span><span class="sxs-lookup"><span data-stu-id="07929-527">String</span></span>|  
|<span data-ttu-id="07929-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="07929-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="07929-529">String</span><span class="sxs-lookup"><span data-stu-id="07929-529">String</span></span>|  
|<span data-ttu-id="07929-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="07929-531">String</span><span class="sxs-lookup"><span data-stu-id="07929-531">String</span></span>|  
|<span data-ttu-id="07929-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-532">COLUMN_NAME</span></span>|<span data-ttu-id="07929-533">String</span><span class="sxs-lookup"><span data-stu-id="07929-533">String</span></span>|  
|<span data-ttu-id="07929-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-534">COLUMN_TYPE</span></span>|<span data-ttu-id="07929-535">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-535">Int16</span></span>|  
|<span data-ttu-id="07929-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-536">DATA_TYPE</span></span>|<span data-ttu-id="07929-537">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-537">Int16</span></span>|  
|<span data-ttu-id="07929-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="07929-538">TYPE_NAME</span></span>|<span data-ttu-id="07929-539">String</span><span class="sxs-lookup"><span data-stu-id="07929-539">String</span></span>|  
|<span data-ttu-id="07929-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="07929-540">COLUMN_SIZE</span></span>|<span data-ttu-id="07929-541">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-541">Int32</span></span>|  
|<span data-ttu-id="07929-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="07929-543">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-543">Int32</span></span>|  
|<span data-ttu-id="07929-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="07929-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="07929-545">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-545">Int16</span></span>|  
|<span data-ttu-id="07929-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="07929-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="07929-547">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-547">Int16</span></span>|  
|<span data-ttu-id="07929-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-548">NULLABLE</span></span>|<span data-ttu-id="07929-549">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-549">Int16</span></span>|  
|<span data-ttu-id="07929-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="07929-550">REMARKS</span></span>|<span data-ttu-id="07929-551">String</span><span class="sxs-lookup"><span data-stu-id="07929-551">String</span></span>|  
|<span data-ttu-id="07929-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="07929-552">COLUMN_DEF</span></span>|<span data-ttu-id="07929-553">String</span><span class="sxs-lookup"><span data-stu-id="07929-553">String</span></span>|  
|<span data-ttu-id="07929-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="07929-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="07929-555">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-555">Int16</span></span>|  
|<span data-ttu-id="07929-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="07929-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="07929-557">Int16</span><span class="sxs-lookup"><span data-stu-id="07929-557">Int16</span></span>|  
|<span data-ttu-id="07929-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="07929-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="07929-559">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-559">Int32</span></span>|  
|<span data-ttu-id="07929-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="07929-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="07929-561">Int32</span><span class="sxs-lookup"><span data-stu-id="07929-561">Int32</span></span>|  
|<span data-ttu-id="07929-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="07929-562">IS_NULLABLE</span></span>|<span data-ttu-id="07929-563">String</span><span class="sxs-lookup"><span data-stu-id="07929-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07929-564">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07929-564">See also</span></span>
- [<span data-ttu-id="07929-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="07929-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
