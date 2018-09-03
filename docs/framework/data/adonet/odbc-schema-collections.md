---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479983"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="c66fd-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="c66fd-102">ODBC Schema Collections</span></span>
<span data-ttu-id="c66fd-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="c66fd-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="c66fd-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="c66fd-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="c66fd-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="c66fd-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c66fd-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="c66fd-106">Tables</span></span>  
  
-   <span data-ttu-id="c66fd-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="c66fd-107">Indexes</span></span>  
  
-   <span data-ttu-id="c66fd-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-108">Columns</span></span>  
  
-   <span data-ttu-id="c66fd-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-109">Procedures</span></span>  
  
-   <span data-ttu-id="c66fd-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c66fd-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c66fd-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c66fd-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c66fd-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-113">Tables and Views</span></span>  
  
|<span data-ttu-id="c66fd-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-114">ColumnName</span></span>|<span data-ttu-id="c66fd-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-116">TABLE_CAT</span></span>|<span data-ttu-id="c66fd-117">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-117">String</span></span>|  
|<span data-ttu-id="c66fd-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-118">TABLE_SCHEM</span></span>|<span data-ttu-id="c66fd-119">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-119">String</span></span>|  
|<span data-ttu-id="c66fd-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-120">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-121">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-121">String</span></span>|  
|<span data-ttu-id="c66fd-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-122">TABLE_TYPE</span></span>|<span data-ttu-id="c66fd-123">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-123">String</span></span>|  
|<span data-ttu-id="c66fd-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-124">REMARKS</span></span>|<span data-ttu-id="c66fd-125">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c66fd-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="c66fd-126">Indexes</span></span>  
  
|<span data-ttu-id="c66fd-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-127">ColumnName</span></span>|<span data-ttu-id="c66fd-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-129">TABLE_CAT</span></span>|<span data-ttu-id="c66fd-130">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-130">String</span></span>|  
|<span data-ttu-id="c66fd-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-131">TABLE_SCHEM</span></span>|<span data-ttu-id="c66fd-132">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-132">String</span></span>|  
|<span data-ttu-id="c66fd-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-133">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-134">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-134">String</span></span>|  
|<span data-ttu-id="c66fd-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="c66fd-135">NON_UNIQUE</span></span>|<span data-ttu-id="c66fd-136">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-136">Int16</span></span>|  
|<span data-ttu-id="c66fd-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="c66fd-138">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-138">String</span></span>|  
|<span data-ttu-id="c66fd-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-139">INDEX_NAME</span></span>|<span data-ttu-id="c66fd-140">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-140">String</span></span>|  
|<span data-ttu-id="c66fd-141">TYP</span><span class="sxs-lookup"><span data-stu-id="c66fd-141">TYPE</span></span>|<span data-ttu-id="c66fd-142">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-142">Int16</span></span>|  
|<span data-ttu-id="c66fd-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-144">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-144">Int16</span></span>|  
|<span data-ttu-id="c66fd-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-145">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-146">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-146">String</span></span>|  
|<span data-ttu-id="c66fd-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="c66fd-147">ASC_OR_DESC</span></span>|<span data-ttu-id="c66fd-148">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-148">String</span></span>|  
|<span data-ttu-id="c66fd-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="c66fd-149">CARDINATLITY</span></span>|<span data-ttu-id="c66fd-150">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-150">Int32</span></span>|  
|<span data-ttu-id="c66fd-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="c66fd-151">PAGES</span></span>|<span data-ttu-id="c66fd-152">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-152">Int32</span></span>|  
|<span data-ttu-id="c66fd-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-153">FILTER_CONDITION</span></span>|<span data-ttu-id="c66fd-154">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-154">String</span></span>|  
|<span data-ttu-id="c66fd-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c66fd-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c66fd-156">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-156">String</span></span>|  
|<span data-ttu-id="c66fd-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-158">Byte</span><span class="sxs-lookup"><span data-stu-id="c66fd-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c66fd-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-159">Columns</span></span>  
  
|<span data-ttu-id="c66fd-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-160">ColumnName</span></span>|<span data-ttu-id="c66fd-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-162">TABLE_CAT</span></span>|<span data-ttu-id="c66fd-163">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-163">String</span></span>|  
|<span data-ttu-id="c66fd-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-164">TABLE_SCHEM</span></span>|<span data-ttu-id="c66fd-165">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-165">String</span></span>|  
|<span data-ttu-id="c66fd-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-166">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-167">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-167">String</span></span>|  
|<span data-ttu-id="c66fd-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-168">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-169">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-169">String</span></span>|  
|<span data-ttu-id="c66fd-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-170">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-171">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-171">Int16</span></span>|  
|<span data-ttu-id="c66fd-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-172">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-173">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-173">String</span></span>|  
|<span data-ttu-id="c66fd-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c66fd-174">COLUMN_SIZE</span></span>|<span data-ttu-id="c66fd-175">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-175">Int32</span></span>|  
|<span data-ttu-id="c66fd-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="c66fd-177">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-177">Int32</span></span>|  
|<span data-ttu-id="c66fd-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c66fd-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c66fd-179">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-179">Int16</span></span>|  
|<span data-ttu-id="c66fd-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c66fd-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c66fd-181">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-181">Int16</span></span>|  
|<span data-ttu-id="c66fd-182">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-182">NULLABLE</span></span>|<span data-ttu-id="c66fd-183">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-183">Int16</span></span>|  
|<span data-ttu-id="c66fd-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-184">REMARKS</span></span>|<span data-ttu-id="c66fd-185">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-185">String</span></span>|  
|<span data-ttu-id="c66fd-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c66fd-186">COLUMN_DEF</span></span>|<span data-ttu-id="c66fd-187">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-187">String</span></span>|  
|<span data-ttu-id="c66fd-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-189">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-189">Int16</span></span>|  
|<span data-ttu-id="c66fd-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c66fd-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c66fd-191">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-191">Int16</span></span>|  
|<span data-ttu-id="c66fd-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c66fd-193">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-193">Int32</span></span>|  
|<span data-ttu-id="c66fd-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-195">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-195">Int32</span></span>|  
|<span data-ttu-id="c66fd-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c66fd-196">IS_NULLABLE</span></span>|<span data-ttu-id="c66fd-197">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-197">String</span></span>|  
|<span data-ttu-id="c66fd-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c66fd-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c66fd-199">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-199">String</span></span>|  
|<span data-ttu-id="c66fd-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c66fd-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c66fd-201">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-201">String</span></span>|  
|<span data-ttu-id="c66fd-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-203">Byte</span><span class="sxs-lookup"><span data-stu-id="c66fd-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c66fd-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-204">Procedures</span></span>  
  
|<span data-ttu-id="c66fd-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-205">ColumnName</span></span>|<span data-ttu-id="c66fd-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="c66fd-208">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-208">String</span></span>|  
|<span data-ttu-id="c66fd-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c66fd-210">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-210">String</span></span>|  
|<span data-ttu-id="c66fd-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-212">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-212">String</span></span>|  
|<span data-ttu-id="c66fd-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-214">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-214">Int32</span></span>|  
|<span data-ttu-id="c66fd-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-216">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-216">Int32</span></span>|  
|<span data-ttu-id="c66fd-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c66fd-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c66fd-218">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-218">Int32</span></span>|  
|<span data-ttu-id="c66fd-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-219">REMARKS</span></span>|<span data-ttu-id="c66fd-220">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-220">String</span></span>|  
|<span data-ttu-id="c66fd-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c66fd-222">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c66fd-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c66fd-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-224">ColumnName</span></span>|<span data-ttu-id="c66fd-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="c66fd-227">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-227">String</span></span>|  
|<span data-ttu-id="c66fd-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c66fd-229">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-229">String</span></span>|  
|<span data-ttu-id="c66fd-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-231">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-231">String</span></span>|  
|<span data-ttu-id="c66fd-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-232">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-233">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-233">String</span></span>|  
|<span data-ttu-id="c66fd-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-234">COLUMN_TYPE</span></span>|<span data-ttu-id="c66fd-235">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-235">Int16</span></span>|  
|<span data-ttu-id="c66fd-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-236">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-237">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-237">Int16</span></span>|  
|<span data-ttu-id="c66fd-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-238">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-239">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-239">String</span></span>|  
|<span data-ttu-id="c66fd-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c66fd-240">COLUMN_SIZE</span></span>|<span data-ttu-id="c66fd-241">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-241">Int32</span></span>|  
|<span data-ttu-id="c66fd-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="c66fd-243">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-243">Int32</span></span>|  
|<span data-ttu-id="c66fd-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c66fd-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c66fd-245">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-245">Int16</span></span>|  
|<span data-ttu-id="c66fd-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c66fd-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c66fd-247">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-247">Int16</span></span>|  
|<span data-ttu-id="c66fd-248">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-248">NULLABLE</span></span>|<span data-ttu-id="c66fd-249">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-249">Int16</span></span>|  
|<span data-ttu-id="c66fd-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-250">REMARKS</span></span>|<span data-ttu-id="c66fd-251">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-251">String</span></span>|  
|<span data-ttu-id="c66fd-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c66fd-252">COLUMN_DEF</span></span>|<span data-ttu-id="c66fd-253">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-253">String</span></span>|  
|<span data-ttu-id="c66fd-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-255">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-255">Int16</span></span>|  
|<span data-ttu-id="c66fd-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c66fd-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c66fd-257">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-257">Int16</span></span>|  
|<span data-ttu-id="c66fd-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c66fd-259">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-259">Int32</span></span>|  
|<span data-ttu-id="c66fd-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-261">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-261">Int32</span></span>|  
|<span data-ttu-id="c66fd-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c66fd-262">IS_NULLABLE</span></span>|<span data-ttu-id="c66fd-263">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-263">String</span></span>|  
|<span data-ttu-id="c66fd-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c66fd-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c66fd-265">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-265">String</span></span>|  
|<span data-ttu-id="c66fd-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c66fd-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c66fd-267">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-267">String</span></span>|  
|<span data-ttu-id="c66fd-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-269">Byte</span><span class="sxs-lookup"><span data-stu-id="c66fd-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c66fd-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c66fd-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c66fd-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-271">ColumnName</span></span>|<span data-ttu-id="c66fd-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="c66fd-274">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-274">String</span></span>|  
|<span data-ttu-id="c66fd-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c66fd-276">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-276">String</span></span>|  
|<span data-ttu-id="c66fd-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-278">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-278">String</span></span>|  
|<span data-ttu-id="c66fd-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-279">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-280">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-280">String</span></span>|  
|<span data-ttu-id="c66fd-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-281">COLUMN_TYPE</span></span>|<span data-ttu-id="c66fd-282">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-282">Int16</span></span>|  
|<span data-ttu-id="c66fd-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-283">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-284">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-284">Int16</span></span>|  
|<span data-ttu-id="c66fd-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-285">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-286">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-286">String</span></span>|  
|<span data-ttu-id="c66fd-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c66fd-287">COLUMN_SIZE</span></span>|<span data-ttu-id="c66fd-288">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-288">Int32</span></span>|  
|<span data-ttu-id="c66fd-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="c66fd-290">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-290">Int32</span></span>|  
|<span data-ttu-id="c66fd-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c66fd-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c66fd-292">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-292">Int16</span></span>|  
|<span data-ttu-id="c66fd-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c66fd-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c66fd-294">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-294">Int16</span></span>|  
|<span data-ttu-id="c66fd-295">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-295">NULLABLE</span></span>|<span data-ttu-id="c66fd-296">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-296">Int16</span></span>|  
|<span data-ttu-id="c66fd-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-297">REMARKS</span></span>|<span data-ttu-id="c66fd-298">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-298">String</span></span>|  
|<span data-ttu-id="c66fd-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c66fd-299">COLUMN_DEF</span></span>|<span data-ttu-id="c66fd-300">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-300">String</span></span>|  
|<span data-ttu-id="c66fd-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-302">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-302">Int16</span></span>|  
|<span data-ttu-id="c66fd-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c66fd-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c66fd-304">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-304">Int16</span></span>|  
|<span data-ttu-id="c66fd-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c66fd-306">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-306">Int32</span></span>|  
|<span data-ttu-id="c66fd-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-308">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-308">Int32</span></span>|  
|<span data-ttu-id="c66fd-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c66fd-309">IS_NULLABLE</span></span>|<span data-ttu-id="c66fd-310">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-310">String</span></span>|  
|<span data-ttu-id="c66fd-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c66fd-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c66fd-312">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-312">String</span></span>|  
|<span data-ttu-id="c66fd-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c66fd-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c66fd-314">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-314">String</span></span>|  
|<span data-ttu-id="c66fd-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-316">Byte</span><span class="sxs-lookup"><span data-stu-id="c66fd-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="c66fd-317">Sterownik ODBC firmy Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="c66fd-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="c66fd-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="c66fd-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c66fd-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="c66fd-319">Tables</span></span>  
  
-   <span data-ttu-id="c66fd-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-320">Columns</span></span>  
  
-   <span data-ttu-id="c66fd-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-321">Procedures</span></span>  
  
-   <span data-ttu-id="c66fd-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c66fd-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c66fd-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c66fd-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-324">Views</span></span>  
  
-   <span data-ttu-id="c66fd-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="c66fd-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c66fd-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-326">Tables and Views</span></span>  
  
|<span data-ttu-id="c66fd-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-327">ColumnName</span></span>|<span data-ttu-id="c66fd-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-330">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-330">String</span></span>|  
|<span data-ttu-id="c66fd-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-331">TABLE_OWNER</span></span>|<span data-ttu-id="c66fd-332">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-332">String</span></span>|  
|<span data-ttu-id="c66fd-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-333">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-334">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-334">String</span></span>|  
|<span data-ttu-id="c66fd-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-335">TABLE_TYPE</span></span>|<span data-ttu-id="c66fd-336">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-336">String</span></span>|  
|<span data-ttu-id="c66fd-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-337">REMARKS</span></span>|<span data-ttu-id="c66fd-338">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c66fd-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-339">Columns</span></span>  
  
|<span data-ttu-id="c66fd-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-340">ColumnName</span></span>|<span data-ttu-id="c66fd-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-343">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-343">String</span></span>|  
|<span data-ttu-id="c66fd-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-344">TABLE_OWNER</span></span>|<span data-ttu-id="c66fd-345">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-345">String</span></span>|  
|<span data-ttu-id="c66fd-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-346">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-347">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-347">String</span></span>|  
|<span data-ttu-id="c66fd-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-348">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-349">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-349">String</span></span>|  
|<span data-ttu-id="c66fd-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-350">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-351">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-351">Int16</span></span>|  
|<span data-ttu-id="c66fd-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-352">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-353">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-353">String</span></span>|  
|<span data-ttu-id="c66fd-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="c66fd-354">PRECISION</span></span>|<span data-ttu-id="c66fd-355">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-355">Int32</span></span>|  
|<span data-ttu-id="c66fd-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="c66fd-356">LENGTH</span></span>|<span data-ttu-id="c66fd-357">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-357">Int32</span></span>|  
|<span data-ttu-id="c66fd-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="c66fd-358">SCALE</span></span>|<span data-ttu-id="c66fd-359">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-359">Int16</span></span>|  
|<span data-ttu-id="c66fd-360">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="c66fd-360">RADIX</span></span>|<span data-ttu-id="c66fd-361">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-361">Int16</span></span>|  
|<span data-ttu-id="c66fd-362">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-362">NULLABLE</span></span>|<span data-ttu-id="c66fd-363">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-363">Int16</span></span>|  
|<span data-ttu-id="c66fd-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-364">REMARKS</span></span>|<span data-ttu-id="c66fd-365">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-365">String</span></span>|  
|<span data-ttu-id="c66fd-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-367">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c66fd-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-368">Procedures</span></span>  
  
|<span data-ttu-id="c66fd-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-369">ColumnName</span></span>|<span data-ttu-id="c66fd-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-372">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-372">String</span></span>|  
|<span data-ttu-id="c66fd-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c66fd-374">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-374">String</span></span>|  
|<span data-ttu-id="c66fd-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-376">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-376">String</span></span>|  
|<span data-ttu-id="c66fd-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-378">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-378">Int16</span></span>|  
|<span data-ttu-id="c66fd-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-380">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-380">Int16</span></span>|  
|<span data-ttu-id="c66fd-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c66fd-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c66fd-382">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-382">Int16</span></span>|  
|<span data-ttu-id="c66fd-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-383">REMARKS</span></span>|<span data-ttu-id="c66fd-384">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-384">String</span></span>|  
|<span data-ttu-id="c66fd-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c66fd-386">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c66fd-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c66fd-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-388">ColumnName</span></span>|<span data-ttu-id="c66fd-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-391">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-391">String</span></span>|  
|<span data-ttu-id="c66fd-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c66fd-393">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-393">String</span></span>|  
|<span data-ttu-id="c66fd-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-395">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-395">String</span></span>|  
|<span data-ttu-id="c66fd-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-396">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-397">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-397">String</span></span>|  
|<span data-ttu-id="c66fd-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-398">COLUMN_TYPE</span></span>|<span data-ttu-id="c66fd-399">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-399">Int16</span></span>|  
|<span data-ttu-id="c66fd-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-400">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-401">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-401">Int16</span></span>|  
|<span data-ttu-id="c66fd-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-402">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-403">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-403">String</span></span>|  
|<span data-ttu-id="c66fd-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="c66fd-404">PRECISION</span></span>|<span data-ttu-id="c66fd-405">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-405">Int32</span></span>|  
|<span data-ttu-id="c66fd-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="c66fd-406">LENGTH</span></span>|<span data-ttu-id="c66fd-407">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-407">Int32</span></span>|  
|<span data-ttu-id="c66fd-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="c66fd-408">SCALE</span></span>|<span data-ttu-id="c66fd-409">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-409">Int16</span></span>|  
|<span data-ttu-id="c66fd-410">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="c66fd-410">RADIX</span></span>|<span data-ttu-id="c66fd-411">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-411">Int16</span></span>|  
|<span data-ttu-id="c66fd-412">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-412">NULLABLE</span></span>|<span data-ttu-id="c66fd-413">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-413">Int16</span></span>|  
|<span data-ttu-id="c66fd-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-414">REMARKS</span></span>|<span data-ttu-id="c66fd-415">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-415">String</span></span>|  
|<span data-ttu-id="c66fd-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="c66fd-416">OVERLOAD</span></span>|<span data-ttu-id="c66fd-417">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-417">Int32</span></span>|  
|<span data-ttu-id="c66fd-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-419">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="c66fd-420">Sterownik ODBC firmy Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="c66fd-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="c66fd-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="c66fd-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c66fd-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="c66fd-422">Tables</span></span>  
  
-   <span data-ttu-id="c66fd-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="c66fd-423">Indexes</span></span>  
  
-   <span data-ttu-id="c66fd-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-424">Columns</span></span>  
  
-   <span data-ttu-id="c66fd-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-425">Procedures</span></span>  
  
-   <span data-ttu-id="c66fd-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c66fd-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c66fd-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c66fd-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c66fd-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="c66fd-429">Tables and Views</span></span>  
  
|<span data-ttu-id="c66fd-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-430">ColumnName</span></span>|<span data-ttu-id="c66fd-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-433">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-433">String</span></span>|  
|<span data-ttu-id="c66fd-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-434">TABLE_OWNER</span></span>|<span data-ttu-id="c66fd-435">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-435">String</span></span>|  
|<span data-ttu-id="c66fd-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-436">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-437">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-437">String</span></span>|  
|<span data-ttu-id="c66fd-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-438">TABLE_TYPE</span></span>|<span data-ttu-id="c66fd-439">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-439">String</span></span>|  
|<span data-ttu-id="c66fd-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-440">REMARKS</span></span>|<span data-ttu-id="c66fd-441">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c66fd-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-442">Columns</span></span>  
  
|<span data-ttu-id="c66fd-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-443">ColumnName</span></span>|<span data-ttu-id="c66fd-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-446">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-446">String</span></span>|  
|<span data-ttu-id="c66fd-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-447">TABLE_OWNER</span></span>|<span data-ttu-id="c66fd-448">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-448">String</span></span>|  
|<span data-ttu-id="c66fd-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-449">TABLE_NAME</span></span>|<span data-ttu-id="c66fd-450">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-450">String</span></span>|  
|<span data-ttu-id="c66fd-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-451">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-452">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-452">String</span></span>|  
|<span data-ttu-id="c66fd-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-453">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-454">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-454">Int16</span></span>|  
|<span data-ttu-id="c66fd-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-455">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-456">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-456">String</span></span>|  
|<span data-ttu-id="c66fd-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="c66fd-457">PRECISION</span></span>|<span data-ttu-id="c66fd-458">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-458">Int32</span></span>|  
|<span data-ttu-id="c66fd-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="c66fd-459">LENGTH</span></span>|<span data-ttu-id="c66fd-460">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-460">Int32</span></span>|  
|<span data-ttu-id="c66fd-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="c66fd-461">SCALE</span></span>|<span data-ttu-id="c66fd-462">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-462">Int16</span></span>|  
|<span data-ttu-id="c66fd-463">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="c66fd-463">RADIX</span></span>|<span data-ttu-id="c66fd-464">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-464">Int16</span></span>|  
|<span data-ttu-id="c66fd-465">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-465">NULLABLE</span></span>|<span data-ttu-id="c66fd-466">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-466">Int16</span></span>|  
|<span data-ttu-id="c66fd-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-467">REMARKS</span></span>|<span data-ttu-id="c66fd-468">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-468">String</span></span>|  
|<span data-ttu-id="c66fd-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-470">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c66fd-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="c66fd-471">Procedures</span></span>  
  
|<span data-ttu-id="c66fd-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-472">ColumnName</span></span>|<span data-ttu-id="c66fd-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-475">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-475">String</span></span>|  
|<span data-ttu-id="c66fd-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c66fd-477">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-477">String</span></span>|  
|<span data-ttu-id="c66fd-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-479">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-479">String</span></span>|  
|<span data-ttu-id="c66fd-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-481">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-481">Int16</span></span>|  
|<span data-ttu-id="c66fd-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c66fd-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c66fd-483">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-483">Int16</span></span>|  
|<span data-ttu-id="c66fd-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c66fd-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c66fd-485">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-485">Int16</span></span>|  
|<span data-ttu-id="c66fd-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-486">REMARKS</span></span>|<span data-ttu-id="c66fd-487">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-487">String</span></span>|  
|<span data-ttu-id="c66fd-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c66fd-489">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c66fd-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c66fd-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c66fd-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-491">ColumnName</span></span>|<span data-ttu-id="c66fd-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c66fd-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c66fd-494">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-494">String</span></span>|  
|<span data-ttu-id="c66fd-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c66fd-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c66fd-496">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-496">String</span></span>|  
|<span data-ttu-id="c66fd-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-498">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-498">String</span></span>|  
|<span data-ttu-id="c66fd-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-499">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-500">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-500">String</span></span>|  
|<span data-ttu-id="c66fd-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-501">COLUMN_TYPE</span></span>|<span data-ttu-id="c66fd-502">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-502">Int16</span></span>|  
|<span data-ttu-id="c66fd-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-503">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-504">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-504">Int16</span></span>|  
|<span data-ttu-id="c66fd-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-505">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-506">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-506">String</span></span>|  
|<span data-ttu-id="c66fd-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="c66fd-507">PRECISION</span></span>|<span data-ttu-id="c66fd-508">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-508">Int32</span></span>|  
|<span data-ttu-id="c66fd-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="c66fd-509">LENGTH</span></span>|<span data-ttu-id="c66fd-510">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-510">Int32</span></span>|  
|<span data-ttu-id="c66fd-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="c66fd-511">SCALE</span></span>|<span data-ttu-id="c66fd-512">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-512">Int16</span></span>|  
|<span data-ttu-id="c66fd-513">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="c66fd-513">RADIX</span></span>|<span data-ttu-id="c66fd-514">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-514">Int16</span></span>|  
|<span data-ttu-id="c66fd-515">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-515">NULLABLE</span></span>|<span data-ttu-id="c66fd-516">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-516">Int16</span></span>|  
|<span data-ttu-id="c66fd-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-517">REMARKS</span></span>|<span data-ttu-id="c66fd-518">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-518">String</span></span>|  
|<span data-ttu-id="c66fd-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="c66fd-519">OVERLOAD</span></span>|<span data-ttu-id="c66fd-520">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-520">Int32</span></span>|  
|<span data-ttu-id="c66fd-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-522">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c66fd-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c66fd-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c66fd-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="c66fd-524">ColumnName</span></span>|<span data-ttu-id="c66fd-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c66fd-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c66fd-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="c66fd-527">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-527">String</span></span>|  
|<span data-ttu-id="c66fd-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c66fd-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c66fd-529">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-529">String</span></span>|  
|<span data-ttu-id="c66fd-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="c66fd-531">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-531">String</span></span>|  
|<span data-ttu-id="c66fd-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-532">COLUMN_NAME</span></span>|<span data-ttu-id="c66fd-533">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-533">String</span></span>|  
|<span data-ttu-id="c66fd-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-534">COLUMN_TYPE</span></span>|<span data-ttu-id="c66fd-535">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-535">Int16</span></span>|  
|<span data-ttu-id="c66fd-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-536">DATA_TYPE</span></span>|<span data-ttu-id="c66fd-537">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-537">Int16</span></span>|  
|<span data-ttu-id="c66fd-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c66fd-538">TYPE_NAME</span></span>|<span data-ttu-id="c66fd-539">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-539">String</span></span>|  
|<span data-ttu-id="c66fd-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c66fd-540">COLUMN_SIZE</span></span>|<span data-ttu-id="c66fd-541">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-541">Int32</span></span>|  
|<span data-ttu-id="c66fd-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="c66fd-543">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-543">Int32</span></span>|  
|<span data-ttu-id="c66fd-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c66fd-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c66fd-545">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-545">Int16</span></span>|  
|<span data-ttu-id="c66fd-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c66fd-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c66fd-547">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-547">Int16</span></span>|  
|<span data-ttu-id="c66fd-548">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="c66fd-548">NULLABLE</span></span>|<span data-ttu-id="c66fd-549">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-549">Int16</span></span>|  
|<span data-ttu-id="c66fd-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="c66fd-550">REMARKS</span></span>|<span data-ttu-id="c66fd-551">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-551">String</span></span>|  
|<span data-ttu-id="c66fd-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c66fd-552">COLUMN_DEF</span></span>|<span data-ttu-id="c66fd-553">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-553">String</span></span>|  
|<span data-ttu-id="c66fd-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c66fd-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c66fd-555">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-555">Int16</span></span>|  
|<span data-ttu-id="c66fd-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c66fd-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c66fd-557">Int16</span><span class="sxs-lookup"><span data-stu-id="c66fd-557">Int16</span></span>|  
|<span data-ttu-id="c66fd-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c66fd-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c66fd-559">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-559">Int32</span></span>|  
|<span data-ttu-id="c66fd-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c66fd-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="c66fd-561">Int32</span><span class="sxs-lookup"><span data-stu-id="c66fd-561">Int32</span></span>|  
|<span data-ttu-id="c66fd-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c66fd-562">IS_NULLABLE</span></span>|<span data-ttu-id="c66fd-563">String</span><span class="sxs-lookup"><span data-stu-id="c66fd-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c66fd-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c66fd-564">See Also</span></span>  
 [<span data-ttu-id="c66fd-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c66fd-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
