---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877534"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="cbbd7-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="cbbd7-102">ODBC Schema Collections</span></span>
<span data-ttu-id="cbbd7-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="cbbd7-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="cbbd7-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="cbbd7-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="cbbd7-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbbd7-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="cbbd7-106">Tables</span></span>  
  
-   <span data-ttu-id="cbbd7-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="cbbd7-107">Indexes</span></span>  
  
-   <span data-ttu-id="cbbd7-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-108">Columns</span></span>  
  
-   <span data-ttu-id="cbbd7-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-109">Procedures</span></span>  
  
-   <span data-ttu-id="cbbd7-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbbd7-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbbd7-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbbd7-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbbd7-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-113">Tables and Views</span></span>  
  
|<span data-ttu-id="cbbd7-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-114">ColumnName</span></span>|<span data-ttu-id="cbbd7-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-116">TABLE_CAT</span></span>|<span data-ttu-id="cbbd7-117">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-117">String</span></span>|  
|<span data-ttu-id="cbbd7-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-118">TABLE_SCHEM</span></span>|<span data-ttu-id="cbbd7-119">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-119">String</span></span>|  
|<span data-ttu-id="cbbd7-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-120">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-121">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-121">String</span></span>|  
|<span data-ttu-id="cbbd7-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-122">TABLE_TYPE</span></span>|<span data-ttu-id="cbbd7-123">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-123">String</span></span>|  
|<span data-ttu-id="cbbd7-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-124">REMARKS</span></span>|<span data-ttu-id="cbbd7-125">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cbbd7-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="cbbd7-126">Indexes</span></span>  
  
|<span data-ttu-id="cbbd7-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-127">ColumnName</span></span>|<span data-ttu-id="cbbd7-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-129">TABLE_CAT</span></span>|<span data-ttu-id="cbbd7-130">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-130">String</span></span>|  
|<span data-ttu-id="cbbd7-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-131">TABLE_SCHEM</span></span>|<span data-ttu-id="cbbd7-132">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-132">String</span></span>|  
|<span data-ttu-id="cbbd7-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-133">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-134">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-134">String</span></span>|  
|<span data-ttu-id="cbbd7-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-135">NON_UNIQUE</span></span>|<span data-ttu-id="cbbd7-136">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-136">Int16</span></span>|  
|<span data-ttu-id="cbbd7-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-138">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-138">String</span></span>|  
|<span data-ttu-id="cbbd7-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-139">INDEX_NAME</span></span>|<span data-ttu-id="cbbd7-140">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-140">String</span></span>|  
|<span data-ttu-id="cbbd7-141">TYP</span><span class="sxs-lookup"><span data-stu-id="cbbd7-141">TYPE</span></span>|<span data-ttu-id="cbbd7-142">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-142">Int16</span></span>|  
|<span data-ttu-id="cbbd7-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-144">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-144">Int16</span></span>|  
|<span data-ttu-id="cbbd7-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-145">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-146">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-146">String</span></span>|  
|<span data-ttu-id="cbbd7-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="cbbd7-147">ASC_OR_DESC</span></span>|<span data-ttu-id="cbbd7-148">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-148">String</span></span>|  
|<span data-ttu-id="cbbd7-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-149">CARDINATLITY</span></span>|<span data-ttu-id="cbbd7-150">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-150">Int32</span></span>|  
|<span data-ttu-id="cbbd7-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-151">PAGES</span></span>|<span data-ttu-id="cbbd7-152">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-152">Int32</span></span>|  
|<span data-ttu-id="cbbd7-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-153">FILTER_CONDITION</span></span>|<span data-ttu-id="cbbd7-154">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-154">String</span></span>|  
|<span data-ttu-id="cbbd7-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbbd7-156">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-156">String</span></span>|  
|<span data-ttu-id="cbbd7-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-158">Byte</span><span class="sxs-lookup"><span data-stu-id="cbbd7-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbbd7-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-159">Columns</span></span>  
  
|<span data-ttu-id="cbbd7-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-160">ColumnName</span></span>|<span data-ttu-id="cbbd7-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-162">TABLE_CAT</span></span>|<span data-ttu-id="cbbd7-163">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-163">String</span></span>|  
|<span data-ttu-id="cbbd7-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-164">TABLE_SCHEM</span></span>|<span data-ttu-id="cbbd7-165">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-165">String</span></span>|  
|<span data-ttu-id="cbbd7-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-166">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-167">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-167">String</span></span>|  
|<span data-ttu-id="cbbd7-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-168">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-169">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-169">String</span></span>|  
|<span data-ttu-id="cbbd7-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-170">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-171">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-171">Int16</span></span>|  
|<span data-ttu-id="cbbd7-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-172">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-173">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-173">String</span></span>|  
|<span data-ttu-id="cbbd7-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-174">COLUMN_SIZE</span></span>|<span data-ttu-id="cbbd7-175">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-175">Int32</span></span>|  
|<span data-ttu-id="cbbd7-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbbd7-177">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-177">Int32</span></span>|  
|<span data-ttu-id="cbbd7-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbbd7-179">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-179">Int16</span></span>|  
|<span data-ttu-id="cbbd7-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbbd7-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbbd7-181">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-181">Int16</span></span>|  
|<span data-ttu-id="cbbd7-182">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-182">NULLABLE</span></span>|<span data-ttu-id="cbbd7-183">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-183">Int16</span></span>|  
|<span data-ttu-id="cbbd7-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-184">REMARKS</span></span>|<span data-ttu-id="cbbd7-185">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-185">String</span></span>|  
|<span data-ttu-id="cbbd7-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbbd7-186">COLUMN_DEF</span></span>|<span data-ttu-id="cbbd7-187">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-187">String</span></span>|  
|<span data-ttu-id="cbbd7-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-189">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-189">Int16</span></span>|  
|<span data-ttu-id="cbbd7-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbbd7-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbbd7-191">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-191">Int16</span></span>|  
|<span data-ttu-id="cbbd7-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbbd7-193">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-193">Int32</span></span>|  
|<span data-ttu-id="cbbd7-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-195">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-195">Int32</span></span>|  
|<span data-ttu-id="cbbd7-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-196">IS_NULLABLE</span></span>|<span data-ttu-id="cbbd7-197">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-197">String</span></span>|  
|<span data-ttu-id="cbbd7-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbbd7-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbbd7-199">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-199">String</span></span>|  
|<span data-ttu-id="cbbd7-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbbd7-201">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-201">String</span></span>|  
|<span data-ttu-id="cbbd7-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-203">Byte</span><span class="sxs-lookup"><span data-stu-id="cbbd7-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbbd7-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-204">Procedures</span></span>  
  
|<span data-ttu-id="cbbd7-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-205">ColumnName</span></span>|<span data-ttu-id="cbbd7-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbbd7-208">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-208">String</span></span>|  
|<span data-ttu-id="cbbd7-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbbd7-210">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-210">String</span></span>|  
|<span data-ttu-id="cbbd7-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-212">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-212">String</span></span>|  
|<span data-ttu-id="cbbd7-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-214">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-214">Int32</span></span>|  
|<span data-ttu-id="cbbd7-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-216">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-216">Int32</span></span>|  
|<span data-ttu-id="cbbd7-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbbd7-218">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-218">Int32</span></span>|  
|<span data-ttu-id="cbbd7-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-219">REMARKS</span></span>|<span data-ttu-id="cbbd7-220">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-220">String</span></span>|  
|<span data-ttu-id="cbbd7-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbbd7-222">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbbd7-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbbd7-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-224">ColumnName</span></span>|<span data-ttu-id="cbbd7-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbbd7-227">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-227">String</span></span>|  
|<span data-ttu-id="cbbd7-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbbd7-229">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-229">String</span></span>|  
|<span data-ttu-id="cbbd7-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-231">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-231">String</span></span>|  
|<span data-ttu-id="cbbd7-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-232">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-233">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-233">String</span></span>|  
|<span data-ttu-id="cbbd7-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-234">COLUMN_TYPE</span></span>|<span data-ttu-id="cbbd7-235">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-235">Int16</span></span>|  
|<span data-ttu-id="cbbd7-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-236">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-237">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-237">Int16</span></span>|  
|<span data-ttu-id="cbbd7-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-238">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-239">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-239">String</span></span>|  
|<span data-ttu-id="cbbd7-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-240">COLUMN_SIZE</span></span>|<span data-ttu-id="cbbd7-241">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-241">Int32</span></span>|  
|<span data-ttu-id="cbbd7-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbbd7-243">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-243">Int32</span></span>|  
|<span data-ttu-id="cbbd7-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbbd7-245">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-245">Int16</span></span>|  
|<span data-ttu-id="cbbd7-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbbd7-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbbd7-247">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-247">Int16</span></span>|  
|<span data-ttu-id="cbbd7-248">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-248">NULLABLE</span></span>|<span data-ttu-id="cbbd7-249">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-249">Int16</span></span>|  
|<span data-ttu-id="cbbd7-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-250">REMARKS</span></span>|<span data-ttu-id="cbbd7-251">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-251">String</span></span>|  
|<span data-ttu-id="cbbd7-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbbd7-252">COLUMN_DEF</span></span>|<span data-ttu-id="cbbd7-253">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-253">String</span></span>|  
|<span data-ttu-id="cbbd7-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-255">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-255">Int16</span></span>|  
|<span data-ttu-id="cbbd7-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbbd7-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbbd7-257">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-257">Int16</span></span>|  
|<span data-ttu-id="cbbd7-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbbd7-259">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-259">Int32</span></span>|  
|<span data-ttu-id="cbbd7-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-261">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-261">Int32</span></span>|  
|<span data-ttu-id="cbbd7-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-262">IS_NULLABLE</span></span>|<span data-ttu-id="cbbd7-263">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-263">String</span></span>|  
|<span data-ttu-id="cbbd7-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbbd7-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbbd7-265">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-265">String</span></span>|  
|<span data-ttu-id="cbbd7-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbbd7-267">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-267">String</span></span>|  
|<span data-ttu-id="cbbd7-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-269">Byte</span><span class="sxs-lookup"><span data-stu-id="cbbd7-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cbbd7-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbbd7-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cbbd7-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-271">ColumnName</span></span>|<span data-ttu-id="cbbd7-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbbd7-274">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-274">String</span></span>|  
|<span data-ttu-id="cbbd7-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbbd7-276">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-276">String</span></span>|  
|<span data-ttu-id="cbbd7-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-278">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-278">String</span></span>|  
|<span data-ttu-id="cbbd7-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-279">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-280">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-280">String</span></span>|  
|<span data-ttu-id="cbbd7-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-281">COLUMN_TYPE</span></span>|<span data-ttu-id="cbbd7-282">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-282">Int16</span></span>|  
|<span data-ttu-id="cbbd7-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-283">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-284">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-284">Int16</span></span>|  
|<span data-ttu-id="cbbd7-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-285">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-286">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-286">String</span></span>|  
|<span data-ttu-id="cbbd7-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-287">COLUMN_SIZE</span></span>|<span data-ttu-id="cbbd7-288">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-288">Int32</span></span>|  
|<span data-ttu-id="cbbd7-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbbd7-290">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-290">Int32</span></span>|  
|<span data-ttu-id="cbbd7-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbbd7-292">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-292">Int16</span></span>|  
|<span data-ttu-id="cbbd7-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbbd7-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbbd7-294">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-294">Int16</span></span>|  
|<span data-ttu-id="cbbd7-295">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-295">NULLABLE</span></span>|<span data-ttu-id="cbbd7-296">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-296">Int16</span></span>|  
|<span data-ttu-id="cbbd7-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-297">REMARKS</span></span>|<span data-ttu-id="cbbd7-298">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-298">String</span></span>|  
|<span data-ttu-id="cbbd7-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbbd7-299">COLUMN_DEF</span></span>|<span data-ttu-id="cbbd7-300">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-300">String</span></span>|  
|<span data-ttu-id="cbbd7-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-302">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-302">Int16</span></span>|  
|<span data-ttu-id="cbbd7-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbbd7-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbbd7-304">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-304">Int16</span></span>|  
|<span data-ttu-id="cbbd7-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbbd7-306">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-306">Int32</span></span>|  
|<span data-ttu-id="cbbd7-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-308">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-308">Int32</span></span>|  
|<span data-ttu-id="cbbd7-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-309">IS_NULLABLE</span></span>|<span data-ttu-id="cbbd7-310">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-310">String</span></span>|  
|<span data-ttu-id="cbbd7-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbbd7-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbbd7-312">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-312">String</span></span>|  
|<span data-ttu-id="cbbd7-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbbd7-314">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-314">String</span></span>|  
|<span data-ttu-id="cbbd7-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-316">Byte</span><span class="sxs-lookup"><span data-stu-id="cbbd7-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="cbbd7-317">Sterownik ODBC firmy Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="cbbd7-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="cbbd7-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbbd7-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="cbbd7-319">Tables</span></span>  
  
-   <span data-ttu-id="cbbd7-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-320">Columns</span></span>  
  
-   <span data-ttu-id="cbbd7-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-321">Procedures</span></span>  
  
-   <span data-ttu-id="cbbd7-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbbd7-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbbd7-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbbd7-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-324">Views</span></span>  
  
-   <span data-ttu-id="cbbd7-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="cbbd7-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbbd7-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-326">Tables and Views</span></span>  
  
|<span data-ttu-id="cbbd7-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-327">ColumnName</span></span>|<span data-ttu-id="cbbd7-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-330">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-330">String</span></span>|  
|<span data-ttu-id="cbbd7-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-331">TABLE_OWNER</span></span>|<span data-ttu-id="cbbd7-332">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-332">String</span></span>|  
|<span data-ttu-id="cbbd7-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-333">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-334">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-334">String</span></span>|  
|<span data-ttu-id="cbbd7-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-335">TABLE_TYPE</span></span>|<span data-ttu-id="cbbd7-336">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-336">String</span></span>|  
|<span data-ttu-id="cbbd7-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-337">REMARKS</span></span>|<span data-ttu-id="cbbd7-338">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbbd7-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-339">Columns</span></span>  
  
|<span data-ttu-id="cbbd7-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-340">ColumnName</span></span>|<span data-ttu-id="cbbd7-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-343">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-343">String</span></span>|  
|<span data-ttu-id="cbbd7-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-344">TABLE_OWNER</span></span>|<span data-ttu-id="cbbd7-345">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-345">String</span></span>|  
|<span data-ttu-id="cbbd7-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-346">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-347">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-347">String</span></span>|  
|<span data-ttu-id="cbbd7-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-348">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-349">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-349">String</span></span>|  
|<span data-ttu-id="cbbd7-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-350">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-351">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-351">Int16</span></span>|  
|<span data-ttu-id="cbbd7-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-352">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-353">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-353">String</span></span>|  
|<span data-ttu-id="cbbd7-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-354">PRECISION</span></span>|<span data-ttu-id="cbbd7-355">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-355">Int32</span></span>|  
|<span data-ttu-id="cbbd7-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="cbbd7-356">LENGTH</span></span>|<span data-ttu-id="cbbd7-357">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-357">Int32</span></span>|  
|<span data-ttu-id="cbbd7-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-358">SCALE</span></span>|<span data-ttu-id="cbbd7-359">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-359">Int16</span></span>|  
|<span data-ttu-id="cbbd7-360">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-360">RADIX</span></span>|<span data-ttu-id="cbbd7-361">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-361">Int16</span></span>|  
|<span data-ttu-id="cbbd7-362">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-362">NULLABLE</span></span>|<span data-ttu-id="cbbd7-363">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-363">Int16</span></span>|  
|<span data-ttu-id="cbbd7-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-364">REMARKS</span></span>|<span data-ttu-id="cbbd7-365">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-365">String</span></span>|  
|<span data-ttu-id="cbbd7-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-367">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbbd7-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-368">Procedures</span></span>  
  
|<span data-ttu-id="cbbd7-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-369">ColumnName</span></span>|<span data-ttu-id="cbbd7-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-372">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-372">String</span></span>|  
|<span data-ttu-id="cbbd7-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbbd7-374">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-374">String</span></span>|  
|<span data-ttu-id="cbbd7-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-376">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-376">String</span></span>|  
|<span data-ttu-id="cbbd7-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-378">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-378">Int16</span></span>|  
|<span data-ttu-id="cbbd7-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-380">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-380">Int16</span></span>|  
|<span data-ttu-id="cbbd7-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbbd7-382">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-382">Int16</span></span>|  
|<span data-ttu-id="cbbd7-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-383">REMARKS</span></span>|<span data-ttu-id="cbbd7-384">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-384">String</span></span>|  
|<span data-ttu-id="cbbd7-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbbd7-386">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbbd7-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbbd7-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-388">ColumnName</span></span>|<span data-ttu-id="cbbd7-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-391">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-391">String</span></span>|  
|<span data-ttu-id="cbbd7-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbbd7-393">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-393">String</span></span>|  
|<span data-ttu-id="cbbd7-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-395">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-395">String</span></span>|  
|<span data-ttu-id="cbbd7-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-396">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-397">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-397">String</span></span>|  
|<span data-ttu-id="cbbd7-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-398">COLUMN_TYPE</span></span>|<span data-ttu-id="cbbd7-399">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-399">Int16</span></span>|  
|<span data-ttu-id="cbbd7-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-400">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-401">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-401">Int16</span></span>|  
|<span data-ttu-id="cbbd7-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-402">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-403">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-403">String</span></span>|  
|<span data-ttu-id="cbbd7-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-404">PRECISION</span></span>|<span data-ttu-id="cbbd7-405">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-405">Int32</span></span>|  
|<span data-ttu-id="cbbd7-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="cbbd7-406">LENGTH</span></span>|<span data-ttu-id="cbbd7-407">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-407">Int32</span></span>|  
|<span data-ttu-id="cbbd7-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-408">SCALE</span></span>|<span data-ttu-id="cbbd7-409">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-409">Int16</span></span>|  
|<span data-ttu-id="cbbd7-410">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-410">RADIX</span></span>|<span data-ttu-id="cbbd7-411">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-411">Int16</span></span>|  
|<span data-ttu-id="cbbd7-412">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-412">NULLABLE</span></span>|<span data-ttu-id="cbbd7-413">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-413">Int16</span></span>|  
|<span data-ttu-id="cbbd7-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-414">REMARKS</span></span>|<span data-ttu-id="cbbd7-415">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-415">String</span></span>|  
|<span data-ttu-id="cbbd7-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-416">OVERLOAD</span></span>|<span data-ttu-id="cbbd7-417">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-417">Int32</span></span>|  
|<span data-ttu-id="cbbd7-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-419">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="cbbd7-420">Sterownik ODBC firmy Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="cbbd7-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="cbbd7-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="cbbd7-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbbd7-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="cbbd7-422">Tables</span></span>  
  
-   <span data-ttu-id="cbbd7-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="cbbd7-423">Indexes</span></span>  
  
-   <span data-ttu-id="cbbd7-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-424">Columns</span></span>  
  
-   <span data-ttu-id="cbbd7-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-425">Procedures</span></span>  
  
-   <span data-ttu-id="cbbd7-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbbd7-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbbd7-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbbd7-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbbd7-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="cbbd7-429">Tables and Views</span></span>  
  
|<span data-ttu-id="cbbd7-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-430">ColumnName</span></span>|<span data-ttu-id="cbbd7-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-433">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-433">String</span></span>|  
|<span data-ttu-id="cbbd7-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-434">TABLE_OWNER</span></span>|<span data-ttu-id="cbbd7-435">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-435">String</span></span>|  
|<span data-ttu-id="cbbd7-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-436">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-437">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-437">String</span></span>|  
|<span data-ttu-id="cbbd7-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-438">TABLE_TYPE</span></span>|<span data-ttu-id="cbbd7-439">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-439">String</span></span>|  
|<span data-ttu-id="cbbd7-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-440">REMARKS</span></span>|<span data-ttu-id="cbbd7-441">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbbd7-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-442">Columns</span></span>  
  
|<span data-ttu-id="cbbd7-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-443">ColumnName</span></span>|<span data-ttu-id="cbbd7-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-446">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-446">String</span></span>|  
|<span data-ttu-id="cbbd7-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-447">TABLE_OWNER</span></span>|<span data-ttu-id="cbbd7-448">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-448">String</span></span>|  
|<span data-ttu-id="cbbd7-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-449">TABLE_NAME</span></span>|<span data-ttu-id="cbbd7-450">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-450">String</span></span>|  
|<span data-ttu-id="cbbd7-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-451">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-452">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-452">String</span></span>|  
|<span data-ttu-id="cbbd7-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-453">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-454">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-454">Int16</span></span>|  
|<span data-ttu-id="cbbd7-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-455">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-456">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-456">String</span></span>|  
|<span data-ttu-id="cbbd7-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-457">PRECISION</span></span>|<span data-ttu-id="cbbd7-458">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-458">Int32</span></span>|  
|<span data-ttu-id="cbbd7-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="cbbd7-459">LENGTH</span></span>|<span data-ttu-id="cbbd7-460">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-460">Int32</span></span>|  
|<span data-ttu-id="cbbd7-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-461">SCALE</span></span>|<span data-ttu-id="cbbd7-462">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-462">Int16</span></span>|  
|<span data-ttu-id="cbbd7-463">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-463">RADIX</span></span>|<span data-ttu-id="cbbd7-464">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-464">Int16</span></span>|  
|<span data-ttu-id="cbbd7-465">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-465">NULLABLE</span></span>|<span data-ttu-id="cbbd7-466">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-466">Int16</span></span>|  
|<span data-ttu-id="cbbd7-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-467">REMARKS</span></span>|<span data-ttu-id="cbbd7-468">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-468">String</span></span>|  
|<span data-ttu-id="cbbd7-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-470">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbbd7-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="cbbd7-471">Procedures</span></span>  
  
|<span data-ttu-id="cbbd7-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-472">ColumnName</span></span>|<span data-ttu-id="cbbd7-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-475">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-475">String</span></span>|  
|<span data-ttu-id="cbbd7-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbbd7-477">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-477">String</span></span>|  
|<span data-ttu-id="cbbd7-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-479">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-479">String</span></span>|  
|<span data-ttu-id="cbbd7-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-481">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-481">Int16</span></span>|  
|<span data-ttu-id="cbbd7-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbbd7-483">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-483">Int16</span></span>|  
|<span data-ttu-id="cbbd7-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbbd7-485">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-485">Int16</span></span>|  
|<span data-ttu-id="cbbd7-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-486">REMARKS</span></span>|<span data-ttu-id="cbbd7-487">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-487">String</span></span>|  
|<span data-ttu-id="cbbd7-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbbd7-489">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbbd7-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbbd7-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbbd7-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-491">ColumnName</span></span>|<span data-ttu-id="cbbd7-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbbd7-494">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-494">String</span></span>|  
|<span data-ttu-id="cbbd7-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbbd7-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbbd7-496">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-496">String</span></span>|  
|<span data-ttu-id="cbbd7-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-498">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-498">String</span></span>|  
|<span data-ttu-id="cbbd7-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-499">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-500">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-500">String</span></span>|  
|<span data-ttu-id="cbbd7-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-501">COLUMN_TYPE</span></span>|<span data-ttu-id="cbbd7-502">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-502">Int16</span></span>|  
|<span data-ttu-id="cbbd7-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-503">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-504">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-504">Int16</span></span>|  
|<span data-ttu-id="cbbd7-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-505">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-506">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-506">String</span></span>|  
|<span data-ttu-id="cbbd7-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-507">PRECISION</span></span>|<span data-ttu-id="cbbd7-508">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-508">Int32</span></span>|  
|<span data-ttu-id="cbbd7-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="cbbd7-509">LENGTH</span></span>|<span data-ttu-id="cbbd7-510">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-510">Int32</span></span>|  
|<span data-ttu-id="cbbd7-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="cbbd7-511">SCALE</span></span>|<span data-ttu-id="cbbd7-512">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-512">Int16</span></span>|  
|<span data-ttu-id="cbbd7-513">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="cbbd7-513">RADIX</span></span>|<span data-ttu-id="cbbd7-514">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-514">Int16</span></span>|  
|<span data-ttu-id="cbbd7-515">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-515">NULLABLE</span></span>|<span data-ttu-id="cbbd7-516">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-516">Int16</span></span>|  
|<span data-ttu-id="cbbd7-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-517">REMARKS</span></span>|<span data-ttu-id="cbbd7-518">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-518">String</span></span>|  
|<span data-ttu-id="cbbd7-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-519">OVERLOAD</span></span>|<span data-ttu-id="cbbd7-520">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-520">Int32</span></span>|  
|<span data-ttu-id="cbbd7-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-522">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cbbd7-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbbd7-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cbbd7-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="cbbd7-524">ColumnName</span></span>|<span data-ttu-id="cbbd7-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbbd7-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbbd7-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbbd7-527">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-527">String</span></span>|  
|<span data-ttu-id="cbbd7-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbbd7-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbbd7-529">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-529">String</span></span>|  
|<span data-ttu-id="cbbd7-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbbd7-531">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-531">String</span></span>|  
|<span data-ttu-id="cbbd7-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-532">COLUMN_NAME</span></span>|<span data-ttu-id="cbbd7-533">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-533">String</span></span>|  
|<span data-ttu-id="cbbd7-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-534">COLUMN_TYPE</span></span>|<span data-ttu-id="cbbd7-535">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-535">Int16</span></span>|  
|<span data-ttu-id="cbbd7-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-536">DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-537">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-537">Int16</span></span>|  
|<span data-ttu-id="cbbd7-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbbd7-538">TYPE_NAME</span></span>|<span data-ttu-id="cbbd7-539">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-539">String</span></span>|  
|<span data-ttu-id="cbbd7-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-540">COLUMN_SIZE</span></span>|<span data-ttu-id="cbbd7-541">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-541">Int32</span></span>|  
|<span data-ttu-id="cbbd7-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbbd7-543">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-543">Int32</span></span>|  
|<span data-ttu-id="cbbd7-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbbd7-545">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-545">Int16</span></span>|  
|<span data-ttu-id="cbbd7-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbbd7-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbbd7-547">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-547">Int16</span></span>|  
|<span data-ttu-id="cbbd7-548">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="cbbd7-548">NULLABLE</span></span>|<span data-ttu-id="cbbd7-549">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-549">Int16</span></span>|  
|<span data-ttu-id="cbbd7-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbbd7-550">REMARKS</span></span>|<span data-ttu-id="cbbd7-551">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-551">String</span></span>|  
|<span data-ttu-id="cbbd7-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbbd7-552">COLUMN_DEF</span></span>|<span data-ttu-id="cbbd7-553">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-553">String</span></span>|  
|<span data-ttu-id="cbbd7-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbbd7-555">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-555">Int16</span></span>|  
|<span data-ttu-id="cbbd7-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbbd7-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbbd7-557">Int16</span><span class="sxs-lookup"><span data-stu-id="cbbd7-557">Int16</span></span>|  
|<span data-ttu-id="cbbd7-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbbd7-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbbd7-559">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-559">Int32</span></span>|  
|<span data-ttu-id="cbbd7-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbbd7-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbbd7-561">Int32</span><span class="sxs-lookup"><span data-stu-id="cbbd7-561">Int32</span></span>|  
|<span data-ttu-id="cbbd7-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbbd7-562">IS_NULLABLE</span></span>|<span data-ttu-id="cbbd7-563">String</span><span class="sxs-lookup"><span data-stu-id="cbbd7-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbbd7-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbbd7-564">See Also</span></span>  
 [<span data-ttu-id="cbbd7-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="cbbd7-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
