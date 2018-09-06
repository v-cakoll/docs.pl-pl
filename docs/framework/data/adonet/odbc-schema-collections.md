---
title: Kolekcje schematów ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43750012"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="59a9a-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="59a9a-102">ODBC Schema Collections</span></span>
<span data-ttu-id="59a9a-103">W tej sekcji omówiono Obsługa kolekcję schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="59a9a-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="59a9a-104">Sterownik ODBC usługi Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="59a9a-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="59a9a-105">Sterownik ODBC firmy Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="59a9a-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="59a9a-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="59a9a-106">Tables</span></span>  
  
-   <span data-ttu-id="59a9a-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="59a9a-107">Indexes</span></span>  
  
-   <span data-ttu-id="59a9a-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-108">Columns</span></span>  
  
-   <span data-ttu-id="59a9a-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-109">Procedures</span></span>  
  
-   <span data-ttu-id="59a9a-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="59a9a-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="59a9a-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="59a9a-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="59a9a-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-113">Tables and Views</span></span>  
  
|<span data-ttu-id="59a9a-114">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-114">ColumnName</span></span>|<span data-ttu-id="59a9a-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-116">TABLE_CAT</span></span>|<span data-ttu-id="59a9a-117">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-117">String</span></span>|  
|<span data-ttu-id="59a9a-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-118">TABLE_SCHEM</span></span>|<span data-ttu-id="59a9a-119">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-119">String</span></span>|  
|<span data-ttu-id="59a9a-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-120">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-121">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-121">String</span></span>|  
|<span data-ttu-id="59a9a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-122">TABLE_TYPE</span></span>|<span data-ttu-id="59a9a-123">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-123">String</span></span>|  
|<span data-ttu-id="59a9a-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-124">REMARKS</span></span>|<span data-ttu-id="59a9a-125">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="59a9a-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="59a9a-126">Indexes</span></span>  
  
|<span data-ttu-id="59a9a-127">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-127">ColumnName</span></span>|<span data-ttu-id="59a9a-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-129">TABLE_CAT</span></span>|<span data-ttu-id="59a9a-130">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-130">String</span></span>|  
|<span data-ttu-id="59a9a-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-131">TABLE_SCHEM</span></span>|<span data-ttu-id="59a9a-132">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-132">String</span></span>|  
|<span data-ttu-id="59a9a-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-133">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-134">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-134">String</span></span>|  
|<span data-ttu-id="59a9a-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="59a9a-135">NON_UNIQUE</span></span>|<span data-ttu-id="59a9a-136">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-136">Int16</span></span>|  
|<span data-ttu-id="59a9a-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="59a9a-138">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-138">String</span></span>|  
|<span data-ttu-id="59a9a-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-139">INDEX_NAME</span></span>|<span data-ttu-id="59a9a-140">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-140">String</span></span>|  
|<span data-ttu-id="59a9a-141">TYP</span><span class="sxs-lookup"><span data-stu-id="59a9a-141">TYPE</span></span>|<span data-ttu-id="59a9a-142">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-142">Int16</span></span>|  
|<span data-ttu-id="59a9a-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-144">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-144">Int16</span></span>|  
|<span data-ttu-id="59a9a-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-145">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-146">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-146">String</span></span>|  
|<span data-ttu-id="59a9a-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="59a9a-147">ASC_OR_DESC</span></span>|<span data-ttu-id="59a9a-148">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-148">String</span></span>|  
|<span data-ttu-id="59a9a-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="59a9a-149">CARDINATLITY</span></span>|<span data-ttu-id="59a9a-150">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-150">Int32</span></span>|  
|<span data-ttu-id="59a9a-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="59a9a-151">PAGES</span></span>|<span data-ttu-id="59a9a-152">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-152">Int32</span></span>|  
|<span data-ttu-id="59a9a-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-153">FILTER_CONDITION</span></span>|<span data-ttu-id="59a9a-154">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-154">String</span></span>|  
|<span data-ttu-id="59a9a-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="59a9a-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="59a9a-156">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-156">String</span></span>|  
|<span data-ttu-id="59a9a-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-158">Byte</span><span class="sxs-lookup"><span data-stu-id="59a9a-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="59a9a-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-159">Columns</span></span>  
  
|<span data-ttu-id="59a9a-160">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-160">ColumnName</span></span>|<span data-ttu-id="59a9a-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-162">TABLE_CAT</span></span>|<span data-ttu-id="59a9a-163">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-163">String</span></span>|  
|<span data-ttu-id="59a9a-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-164">TABLE_SCHEM</span></span>|<span data-ttu-id="59a9a-165">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-165">String</span></span>|  
|<span data-ttu-id="59a9a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-166">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-167">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-167">String</span></span>|  
|<span data-ttu-id="59a9a-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-168">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-169">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-169">String</span></span>|  
|<span data-ttu-id="59a9a-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-170">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-171">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-171">Int16</span></span>|  
|<span data-ttu-id="59a9a-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-172">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-173">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-173">String</span></span>|  
|<span data-ttu-id="59a9a-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="59a9a-174">COLUMN_SIZE</span></span>|<span data-ttu-id="59a9a-175">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-175">Int32</span></span>|  
|<span data-ttu-id="59a9a-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="59a9a-177">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-177">Int32</span></span>|  
|<span data-ttu-id="59a9a-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="59a9a-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="59a9a-179">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-179">Int16</span></span>|  
|<span data-ttu-id="59a9a-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="59a9a-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="59a9a-181">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-181">Int16</span></span>|  
|<span data-ttu-id="59a9a-182">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-182">NULLABLE</span></span>|<span data-ttu-id="59a9a-183">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-183">Int16</span></span>|  
|<span data-ttu-id="59a9a-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-184">REMARKS</span></span>|<span data-ttu-id="59a9a-185">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-185">String</span></span>|  
|<span data-ttu-id="59a9a-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="59a9a-186">COLUMN_DEF</span></span>|<span data-ttu-id="59a9a-187">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-187">String</span></span>|  
|<span data-ttu-id="59a9a-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-189">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-189">Int16</span></span>|  
|<span data-ttu-id="59a9a-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="59a9a-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="59a9a-191">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-191">Int16</span></span>|  
|<span data-ttu-id="59a9a-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="59a9a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-193">Int32</span></span>|  
|<span data-ttu-id="59a9a-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-195">Int32</span></span>|  
|<span data-ttu-id="59a9a-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="59a9a-196">IS_NULLABLE</span></span>|<span data-ttu-id="59a9a-197">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-197">String</span></span>|  
|<span data-ttu-id="59a9a-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="59a9a-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="59a9a-199">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-199">String</span></span>|  
|<span data-ttu-id="59a9a-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="59a9a-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="59a9a-201">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-201">String</span></span>|  
|<span data-ttu-id="59a9a-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-203">Byte</span><span class="sxs-lookup"><span data-stu-id="59a9a-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="59a9a-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-204">Procedures</span></span>  
  
|<span data-ttu-id="59a9a-205">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-205">ColumnName</span></span>|<span data-ttu-id="59a9a-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="59a9a-208">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-208">String</span></span>|  
|<span data-ttu-id="59a9a-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="59a9a-210">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-210">String</span></span>|  
|<span data-ttu-id="59a9a-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-212">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-212">String</span></span>|  
|<span data-ttu-id="59a9a-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-214">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-214">Int32</span></span>|  
|<span data-ttu-id="59a9a-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-216">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-216">Int32</span></span>|  
|<span data-ttu-id="59a9a-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="59a9a-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="59a9a-218">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-218">Int32</span></span>|  
|<span data-ttu-id="59a9a-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-219">REMARKS</span></span>|<span data-ttu-id="59a9a-220">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-220">String</span></span>|  
|<span data-ttu-id="59a9a-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="59a9a-222">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="59a9a-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="59a9a-224">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-224">ColumnName</span></span>|<span data-ttu-id="59a9a-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="59a9a-227">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-227">String</span></span>|  
|<span data-ttu-id="59a9a-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="59a9a-229">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-229">String</span></span>|  
|<span data-ttu-id="59a9a-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-231">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-231">String</span></span>|  
|<span data-ttu-id="59a9a-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-232">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-233">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-233">String</span></span>|  
|<span data-ttu-id="59a9a-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-234">COLUMN_TYPE</span></span>|<span data-ttu-id="59a9a-235">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-235">Int16</span></span>|  
|<span data-ttu-id="59a9a-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-236">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-237">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-237">Int16</span></span>|  
|<span data-ttu-id="59a9a-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-238">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-239">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-239">String</span></span>|  
|<span data-ttu-id="59a9a-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="59a9a-240">COLUMN_SIZE</span></span>|<span data-ttu-id="59a9a-241">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-241">Int32</span></span>|  
|<span data-ttu-id="59a9a-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="59a9a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-243">Int32</span></span>|  
|<span data-ttu-id="59a9a-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="59a9a-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="59a9a-245">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-245">Int16</span></span>|  
|<span data-ttu-id="59a9a-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="59a9a-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="59a9a-247">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-247">Int16</span></span>|  
|<span data-ttu-id="59a9a-248">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-248">NULLABLE</span></span>|<span data-ttu-id="59a9a-249">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-249">Int16</span></span>|  
|<span data-ttu-id="59a9a-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-250">REMARKS</span></span>|<span data-ttu-id="59a9a-251">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-251">String</span></span>|  
|<span data-ttu-id="59a9a-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="59a9a-252">COLUMN_DEF</span></span>|<span data-ttu-id="59a9a-253">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-253">String</span></span>|  
|<span data-ttu-id="59a9a-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-255">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-255">Int16</span></span>|  
|<span data-ttu-id="59a9a-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="59a9a-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="59a9a-257">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-257">Int16</span></span>|  
|<span data-ttu-id="59a9a-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="59a9a-259">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-259">Int32</span></span>|  
|<span data-ttu-id="59a9a-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-261">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-261">Int32</span></span>|  
|<span data-ttu-id="59a9a-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="59a9a-262">IS_NULLABLE</span></span>|<span data-ttu-id="59a9a-263">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-263">String</span></span>|  
|<span data-ttu-id="59a9a-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="59a9a-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="59a9a-265">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-265">String</span></span>|  
|<span data-ttu-id="59a9a-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="59a9a-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="59a9a-267">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-267">String</span></span>|  
|<span data-ttu-id="59a9a-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-269">Byte</span><span class="sxs-lookup"><span data-stu-id="59a9a-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="59a9a-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="59a9a-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="59a9a-271">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-271">ColumnName</span></span>|<span data-ttu-id="59a9a-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="59a9a-274">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-274">String</span></span>|  
|<span data-ttu-id="59a9a-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="59a9a-276">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-276">String</span></span>|  
|<span data-ttu-id="59a9a-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-278">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-278">String</span></span>|  
|<span data-ttu-id="59a9a-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-279">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-280">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-280">String</span></span>|  
|<span data-ttu-id="59a9a-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-281">COLUMN_TYPE</span></span>|<span data-ttu-id="59a9a-282">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-282">Int16</span></span>|  
|<span data-ttu-id="59a9a-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-283">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-284">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-284">Int16</span></span>|  
|<span data-ttu-id="59a9a-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-285">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-286">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-286">String</span></span>|  
|<span data-ttu-id="59a9a-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="59a9a-287">COLUMN_SIZE</span></span>|<span data-ttu-id="59a9a-288">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-288">Int32</span></span>|  
|<span data-ttu-id="59a9a-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="59a9a-290">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-290">Int32</span></span>|  
|<span data-ttu-id="59a9a-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="59a9a-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="59a9a-292">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-292">Int16</span></span>|  
|<span data-ttu-id="59a9a-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="59a9a-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="59a9a-294">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-294">Int16</span></span>|  
|<span data-ttu-id="59a9a-295">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-295">NULLABLE</span></span>|<span data-ttu-id="59a9a-296">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-296">Int16</span></span>|  
|<span data-ttu-id="59a9a-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-297">REMARKS</span></span>|<span data-ttu-id="59a9a-298">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-298">String</span></span>|  
|<span data-ttu-id="59a9a-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="59a9a-299">COLUMN_DEF</span></span>|<span data-ttu-id="59a9a-300">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-300">String</span></span>|  
|<span data-ttu-id="59a9a-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-302">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-302">Int16</span></span>|  
|<span data-ttu-id="59a9a-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="59a9a-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="59a9a-304">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-304">Int16</span></span>|  
|<span data-ttu-id="59a9a-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="59a9a-306">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-306">Int32</span></span>|  
|<span data-ttu-id="59a9a-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-308">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-308">Int32</span></span>|  
|<span data-ttu-id="59a9a-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="59a9a-309">IS_NULLABLE</span></span>|<span data-ttu-id="59a9a-310">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-310">String</span></span>|  
|<span data-ttu-id="59a9a-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="59a9a-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="59a9a-312">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-312">String</span></span>|  
|<span data-ttu-id="59a9a-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="59a9a-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="59a9a-314">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-314">String</span></span>|  
|<span data-ttu-id="59a9a-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-316">Byte</span><span class="sxs-lookup"><span data-stu-id="59a9a-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="59a9a-317">Sterownik ODBC firmy Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="59a9a-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="59a9a-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="59a9a-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="59a9a-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="59a9a-319">Tables</span></span>  
  
-   <span data-ttu-id="59a9a-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-320">Columns</span></span>  
  
-   <span data-ttu-id="59a9a-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-321">Procedures</span></span>  
  
-   <span data-ttu-id="59a9a-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="59a9a-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="59a9a-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="59a9a-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-324">Views</span></span>  
  
-   <span data-ttu-id="59a9a-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="59a9a-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="59a9a-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-326">Tables and Views</span></span>  
  
|<span data-ttu-id="59a9a-327">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-327">ColumnName</span></span>|<span data-ttu-id="59a9a-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-330">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-330">String</span></span>|  
|<span data-ttu-id="59a9a-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-331">TABLE_OWNER</span></span>|<span data-ttu-id="59a9a-332">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-332">String</span></span>|  
|<span data-ttu-id="59a9a-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-333">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-334">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-334">String</span></span>|  
|<span data-ttu-id="59a9a-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-335">TABLE_TYPE</span></span>|<span data-ttu-id="59a9a-336">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-336">String</span></span>|  
|<span data-ttu-id="59a9a-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-337">REMARKS</span></span>|<span data-ttu-id="59a9a-338">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="59a9a-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-339">Columns</span></span>  
  
|<span data-ttu-id="59a9a-340">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-340">ColumnName</span></span>|<span data-ttu-id="59a9a-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-343">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-343">String</span></span>|  
|<span data-ttu-id="59a9a-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-344">TABLE_OWNER</span></span>|<span data-ttu-id="59a9a-345">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-345">String</span></span>|  
|<span data-ttu-id="59a9a-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-346">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-347">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-347">String</span></span>|  
|<span data-ttu-id="59a9a-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-348">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-349">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-349">String</span></span>|  
|<span data-ttu-id="59a9a-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-350">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-351">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-351">Int16</span></span>|  
|<span data-ttu-id="59a9a-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-352">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-353">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-353">String</span></span>|  
|<span data-ttu-id="59a9a-354">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="59a9a-354">PRECISION</span></span>|<span data-ttu-id="59a9a-355">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-355">Int32</span></span>|  
|<span data-ttu-id="59a9a-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="59a9a-356">LENGTH</span></span>|<span data-ttu-id="59a9a-357">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-357">Int32</span></span>|  
|<span data-ttu-id="59a9a-358">SKALA</span><span class="sxs-lookup"><span data-stu-id="59a9a-358">SCALE</span></span>|<span data-ttu-id="59a9a-359">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-359">Int16</span></span>|  
|<span data-ttu-id="59a9a-360">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="59a9a-360">RADIX</span></span>|<span data-ttu-id="59a9a-361">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-361">Int16</span></span>|  
|<span data-ttu-id="59a9a-362">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-362">NULLABLE</span></span>|<span data-ttu-id="59a9a-363">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-363">Int16</span></span>|  
|<span data-ttu-id="59a9a-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-364">REMARKS</span></span>|<span data-ttu-id="59a9a-365">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-365">String</span></span>|  
|<span data-ttu-id="59a9a-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-367">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="59a9a-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-368">Procedures</span></span>  
  
|<span data-ttu-id="59a9a-369">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-369">ColumnName</span></span>|<span data-ttu-id="59a9a-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-372">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-372">String</span></span>|  
|<span data-ttu-id="59a9a-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="59a9a-374">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-374">String</span></span>|  
|<span data-ttu-id="59a9a-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-376">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-376">String</span></span>|  
|<span data-ttu-id="59a9a-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-378">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-378">Int16</span></span>|  
|<span data-ttu-id="59a9a-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-380">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-380">Int16</span></span>|  
|<span data-ttu-id="59a9a-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="59a9a-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="59a9a-382">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-382">Int16</span></span>|  
|<span data-ttu-id="59a9a-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-383">REMARKS</span></span>|<span data-ttu-id="59a9a-384">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-384">String</span></span>|  
|<span data-ttu-id="59a9a-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="59a9a-386">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="59a9a-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="59a9a-388">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-388">ColumnName</span></span>|<span data-ttu-id="59a9a-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-391">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-391">String</span></span>|  
|<span data-ttu-id="59a9a-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="59a9a-393">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-393">String</span></span>|  
|<span data-ttu-id="59a9a-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-395">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-395">String</span></span>|  
|<span data-ttu-id="59a9a-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-396">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-397">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-397">String</span></span>|  
|<span data-ttu-id="59a9a-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-398">COLUMN_TYPE</span></span>|<span data-ttu-id="59a9a-399">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-399">Int16</span></span>|  
|<span data-ttu-id="59a9a-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-400">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-401">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-401">Int16</span></span>|  
|<span data-ttu-id="59a9a-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-402">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-403">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-403">String</span></span>|  
|<span data-ttu-id="59a9a-404">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="59a9a-404">PRECISION</span></span>|<span data-ttu-id="59a9a-405">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-405">Int32</span></span>|  
|<span data-ttu-id="59a9a-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="59a9a-406">LENGTH</span></span>|<span data-ttu-id="59a9a-407">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-407">Int32</span></span>|  
|<span data-ttu-id="59a9a-408">SKALA</span><span class="sxs-lookup"><span data-stu-id="59a9a-408">SCALE</span></span>|<span data-ttu-id="59a9a-409">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-409">Int16</span></span>|  
|<span data-ttu-id="59a9a-410">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="59a9a-410">RADIX</span></span>|<span data-ttu-id="59a9a-411">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-411">Int16</span></span>|  
|<span data-ttu-id="59a9a-412">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-412">NULLABLE</span></span>|<span data-ttu-id="59a9a-413">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-413">Int16</span></span>|  
|<span data-ttu-id="59a9a-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-414">REMARKS</span></span>|<span data-ttu-id="59a9a-415">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-415">String</span></span>|  
|<span data-ttu-id="59a9a-416">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="59a9a-416">OVERLOAD</span></span>|<span data-ttu-id="59a9a-417">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-417">Int32</span></span>|  
|<span data-ttu-id="59a9a-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-419">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="59a9a-420">Sterownik ODBC firmy Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="59a9a-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="59a9a-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="59a9a-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="59a9a-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="59a9a-422">Tables</span></span>  
  
-   <span data-ttu-id="59a9a-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="59a9a-423">Indexes</span></span>  
  
-   <span data-ttu-id="59a9a-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-424">Columns</span></span>  
  
-   <span data-ttu-id="59a9a-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-425">Procedures</span></span>  
  
-   <span data-ttu-id="59a9a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="59a9a-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="59a9a-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="59a9a-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="59a9a-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="59a9a-429">Tables and Views</span></span>  
  
|<span data-ttu-id="59a9a-430">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-430">ColumnName</span></span>|<span data-ttu-id="59a9a-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-433">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-433">String</span></span>|  
|<span data-ttu-id="59a9a-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-434">TABLE_OWNER</span></span>|<span data-ttu-id="59a9a-435">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-435">String</span></span>|  
|<span data-ttu-id="59a9a-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-436">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-437">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-437">String</span></span>|  
|<span data-ttu-id="59a9a-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-438">TABLE_TYPE</span></span>|<span data-ttu-id="59a9a-439">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-439">String</span></span>|  
|<span data-ttu-id="59a9a-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-440">REMARKS</span></span>|<span data-ttu-id="59a9a-441">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="59a9a-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-442">Columns</span></span>  
  
|<span data-ttu-id="59a9a-443">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-443">ColumnName</span></span>|<span data-ttu-id="59a9a-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-446">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-446">String</span></span>|  
|<span data-ttu-id="59a9a-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-447">TABLE_OWNER</span></span>|<span data-ttu-id="59a9a-448">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-448">String</span></span>|  
|<span data-ttu-id="59a9a-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-449">TABLE_NAME</span></span>|<span data-ttu-id="59a9a-450">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-450">String</span></span>|  
|<span data-ttu-id="59a9a-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-451">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-452">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-452">String</span></span>|  
|<span data-ttu-id="59a9a-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-453">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-454">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-454">Int16</span></span>|  
|<span data-ttu-id="59a9a-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-455">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-456">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-456">String</span></span>|  
|<span data-ttu-id="59a9a-457">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="59a9a-457">PRECISION</span></span>|<span data-ttu-id="59a9a-458">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-458">Int32</span></span>|  
|<span data-ttu-id="59a9a-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="59a9a-459">LENGTH</span></span>|<span data-ttu-id="59a9a-460">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-460">Int32</span></span>|  
|<span data-ttu-id="59a9a-461">SKALA</span><span class="sxs-lookup"><span data-stu-id="59a9a-461">SCALE</span></span>|<span data-ttu-id="59a9a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-462">Int16</span></span>|  
|<span data-ttu-id="59a9a-463">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="59a9a-463">RADIX</span></span>|<span data-ttu-id="59a9a-464">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-464">Int16</span></span>|  
|<span data-ttu-id="59a9a-465">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-465">NULLABLE</span></span>|<span data-ttu-id="59a9a-466">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-466">Int16</span></span>|  
|<span data-ttu-id="59a9a-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-467">REMARKS</span></span>|<span data-ttu-id="59a9a-468">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-468">String</span></span>|  
|<span data-ttu-id="59a9a-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-470">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="59a9a-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="59a9a-471">Procedures</span></span>  
  
|<span data-ttu-id="59a9a-472">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-472">ColumnName</span></span>|<span data-ttu-id="59a9a-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-475">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-475">String</span></span>|  
|<span data-ttu-id="59a9a-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="59a9a-477">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-477">String</span></span>|  
|<span data-ttu-id="59a9a-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-479">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-479">String</span></span>|  
|<span data-ttu-id="59a9a-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-481">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-481">Int16</span></span>|  
|<span data-ttu-id="59a9a-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="59a9a-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="59a9a-483">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-483">Int16</span></span>|  
|<span data-ttu-id="59a9a-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="59a9a-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="59a9a-485">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-485">Int16</span></span>|  
|<span data-ttu-id="59a9a-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-486">REMARKS</span></span>|<span data-ttu-id="59a9a-487">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-487">String</span></span>|  
|<span data-ttu-id="59a9a-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="59a9a-489">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="59a9a-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="59a9a-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="59a9a-491">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-491">ColumnName</span></span>|<span data-ttu-id="59a9a-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="59a9a-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="59a9a-494">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-494">String</span></span>|  
|<span data-ttu-id="59a9a-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="59a9a-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="59a9a-496">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-496">String</span></span>|  
|<span data-ttu-id="59a9a-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-498">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-498">String</span></span>|  
|<span data-ttu-id="59a9a-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-499">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-500">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-500">String</span></span>|  
|<span data-ttu-id="59a9a-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-501">COLUMN_TYPE</span></span>|<span data-ttu-id="59a9a-502">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-502">Int16</span></span>|  
|<span data-ttu-id="59a9a-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-503">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-504">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-504">Int16</span></span>|  
|<span data-ttu-id="59a9a-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-505">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-506">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-506">String</span></span>|  
|<span data-ttu-id="59a9a-507">PRECYZJA</span><span class="sxs-lookup"><span data-stu-id="59a9a-507">PRECISION</span></span>|<span data-ttu-id="59a9a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-508">Int32</span></span>|  
|<span data-ttu-id="59a9a-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="59a9a-509">LENGTH</span></span>|<span data-ttu-id="59a9a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-510">Int32</span></span>|  
|<span data-ttu-id="59a9a-511">SKALA</span><span class="sxs-lookup"><span data-stu-id="59a9a-511">SCALE</span></span>|<span data-ttu-id="59a9a-512">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-512">Int16</span></span>|  
|<span data-ttu-id="59a9a-513">PODSTAWY</span><span class="sxs-lookup"><span data-stu-id="59a9a-513">RADIX</span></span>|<span data-ttu-id="59a9a-514">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-514">Int16</span></span>|  
|<span data-ttu-id="59a9a-515">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-515">NULLABLE</span></span>|<span data-ttu-id="59a9a-516">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-516">Int16</span></span>|  
|<span data-ttu-id="59a9a-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-517">REMARKS</span></span>|<span data-ttu-id="59a9a-518">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-518">String</span></span>|  
|<span data-ttu-id="59a9a-519">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="59a9a-519">OVERLOAD</span></span>|<span data-ttu-id="59a9a-520">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-520">Int32</span></span>|  
|<span data-ttu-id="59a9a-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-522">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="59a9a-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="59a9a-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="59a9a-524">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="59a9a-524">ColumnName</span></span>|<span data-ttu-id="59a9a-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="59a9a-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="59a9a-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="59a9a-527">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-527">String</span></span>|  
|<span data-ttu-id="59a9a-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="59a9a-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="59a9a-529">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-529">String</span></span>|  
|<span data-ttu-id="59a9a-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="59a9a-531">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-531">String</span></span>|  
|<span data-ttu-id="59a9a-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-532">COLUMN_NAME</span></span>|<span data-ttu-id="59a9a-533">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-533">String</span></span>|  
|<span data-ttu-id="59a9a-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-534">COLUMN_TYPE</span></span>|<span data-ttu-id="59a9a-535">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-535">Int16</span></span>|  
|<span data-ttu-id="59a9a-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-536">DATA_TYPE</span></span>|<span data-ttu-id="59a9a-537">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-537">Int16</span></span>|  
|<span data-ttu-id="59a9a-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="59a9a-538">TYPE_NAME</span></span>|<span data-ttu-id="59a9a-539">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-539">String</span></span>|  
|<span data-ttu-id="59a9a-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="59a9a-540">COLUMN_SIZE</span></span>|<span data-ttu-id="59a9a-541">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-541">Int32</span></span>|  
|<span data-ttu-id="59a9a-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="59a9a-543">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-543">Int32</span></span>|  
|<span data-ttu-id="59a9a-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="59a9a-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="59a9a-545">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-545">Int16</span></span>|  
|<span data-ttu-id="59a9a-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="59a9a-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="59a9a-547">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-547">Int16</span></span>|  
|<span data-ttu-id="59a9a-548">DOPUSZCZA WARTOŚCI NULL</span><span class="sxs-lookup"><span data-stu-id="59a9a-548">NULLABLE</span></span>|<span data-ttu-id="59a9a-549">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-549">Int16</span></span>|  
|<span data-ttu-id="59a9a-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="59a9a-550">REMARKS</span></span>|<span data-ttu-id="59a9a-551">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-551">String</span></span>|  
|<span data-ttu-id="59a9a-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="59a9a-552">COLUMN_DEF</span></span>|<span data-ttu-id="59a9a-553">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-553">String</span></span>|  
|<span data-ttu-id="59a9a-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="59a9a-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="59a9a-555">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-555">Int16</span></span>|  
|<span data-ttu-id="59a9a-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="59a9a-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="59a9a-557">Int16</span><span class="sxs-lookup"><span data-stu-id="59a9a-557">Int16</span></span>|  
|<span data-ttu-id="59a9a-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="59a9a-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="59a9a-559">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-559">Int32</span></span>|  
|<span data-ttu-id="59a9a-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="59a9a-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="59a9a-561">Int32</span><span class="sxs-lookup"><span data-stu-id="59a9a-561">Int32</span></span>|  
|<span data-ttu-id="59a9a-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="59a9a-562">IS_NULLABLE</span></span>|<span data-ttu-id="59a9a-563">String</span><span class="sxs-lookup"><span data-stu-id="59a9a-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59a9a-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59a9a-564">See Also</span></span>  
 [<span data-ttu-id="59a9a-565">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="59a9a-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
