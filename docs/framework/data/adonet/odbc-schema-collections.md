---
title: "Kolekcje schematów ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="9dd58-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="9dd58-102">ODBC Schema Collections</span></span>
<span data-ttu-id="9dd58-103">W tej sekcji omówiono obsługi kolekcji schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="9dd58-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="9dd58-104">Sterownik ODBC programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="9dd58-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="9dd58-105">Sterownik ODBC programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="9dd58-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9dd58-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="9dd58-106">Tables</span></span>  
  
-   <span data-ttu-id="9dd58-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="9dd58-107">Indexes</span></span>  
  
-   <span data-ttu-id="9dd58-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-108">Columns</span></span>  
  
-   <span data-ttu-id="9dd58-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-109">Procedures</span></span>  
  
-   <span data-ttu-id="9dd58-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9dd58-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9dd58-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9dd58-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9dd58-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-113">Tables and Views</span></span>  
  
|<span data-ttu-id="9dd58-114">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-114">ColumnName</span></span>|<span data-ttu-id="9dd58-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-116">TABLE_CAT</span></span>|<span data-ttu-id="9dd58-117">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-117">String</span></span>|  
|<span data-ttu-id="9dd58-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-118">TABLE_SCHEM</span></span>|<span data-ttu-id="9dd58-119">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-119">String</span></span>|  
|<span data-ttu-id="9dd58-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-120">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-121">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-121">String</span></span>|  
|<span data-ttu-id="9dd58-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-122">TABLE_TYPE</span></span>|<span data-ttu-id="9dd58-123">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-123">String</span></span>|  
|<span data-ttu-id="9dd58-124">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-124">REMARKS</span></span>|<span data-ttu-id="9dd58-125">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9dd58-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="9dd58-126">Indexes</span></span>  
  
|<span data-ttu-id="9dd58-127">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-127">ColumnName</span></span>|<span data-ttu-id="9dd58-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-129">TABLE_CAT</span></span>|<span data-ttu-id="9dd58-130">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-130">String</span></span>|  
|<span data-ttu-id="9dd58-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-131">TABLE_SCHEM</span></span>|<span data-ttu-id="9dd58-132">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-132">String</span></span>|  
|<span data-ttu-id="9dd58-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-133">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-134">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-134">String</span></span>|  
|<span data-ttu-id="9dd58-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="9dd58-135">NON_UNIQUE</span></span>|<span data-ttu-id="9dd58-136">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-136">Int16</span></span>|  
|<span data-ttu-id="9dd58-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="9dd58-138">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-138">String</span></span>|  
|<span data-ttu-id="9dd58-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-139">INDEX_NAME</span></span>|<span data-ttu-id="9dd58-140">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-140">String</span></span>|  
|<span data-ttu-id="9dd58-141">TYP</span><span class="sxs-lookup"><span data-stu-id="9dd58-141">TYPE</span></span>|<span data-ttu-id="9dd58-142">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-142">Int16</span></span>|  
|<span data-ttu-id="9dd58-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-144">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-144">Int16</span></span>|  
|<span data-ttu-id="9dd58-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-145">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-146">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-146">String</span></span>|  
|<span data-ttu-id="9dd58-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="9dd58-147">ASC_OR_DESC</span></span>|<span data-ttu-id="9dd58-148">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-148">String</span></span>|  
|<span data-ttu-id="9dd58-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="9dd58-149">CARDINATLITY</span></span>|<span data-ttu-id="9dd58-150">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-150">Int32</span></span>|  
|<span data-ttu-id="9dd58-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="9dd58-151">PAGES</span></span>|<span data-ttu-id="9dd58-152">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-152">Int32</span></span>|  
|<span data-ttu-id="9dd58-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-153">FILTER_CONDITION</span></span>|<span data-ttu-id="9dd58-154">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-154">String</span></span>|  
|<span data-ttu-id="9dd58-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9dd58-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9dd58-156">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-156">String</span></span>|  
|<span data-ttu-id="9dd58-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-158">Byte</span><span class="sxs-lookup"><span data-stu-id="9dd58-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9dd58-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-159">Columns</span></span>  
  
|<span data-ttu-id="9dd58-160">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-160">ColumnName</span></span>|<span data-ttu-id="9dd58-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-162">TABLE_CAT</span></span>|<span data-ttu-id="9dd58-163">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-163">String</span></span>|  
|<span data-ttu-id="9dd58-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-164">TABLE_SCHEM</span></span>|<span data-ttu-id="9dd58-165">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-165">String</span></span>|  
|<span data-ttu-id="9dd58-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-166">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-167">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-167">String</span></span>|  
|<span data-ttu-id="9dd58-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-168">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-169">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-169">String</span></span>|  
|<span data-ttu-id="9dd58-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-170">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-171">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-171">Int16</span></span>|  
|<span data-ttu-id="9dd58-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-172">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-173">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-173">String</span></span>|  
|<span data-ttu-id="9dd58-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9dd58-174">COLUMN_SIZE</span></span>|<span data-ttu-id="9dd58-175">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-175">Int32</span></span>|  
|<span data-ttu-id="9dd58-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="9dd58-177">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-177">Int32</span></span>|  
|<span data-ttu-id="9dd58-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9dd58-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9dd58-179">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-179">Int16</span></span>|  
|<span data-ttu-id="9dd58-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9dd58-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9dd58-181">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-181">Int16</span></span>|  
|<span data-ttu-id="9dd58-182">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-182">NULLABLE</span></span>|<span data-ttu-id="9dd58-183">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-183">Int16</span></span>|  
|<span data-ttu-id="9dd58-184">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-184">REMARKS</span></span>|<span data-ttu-id="9dd58-185">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-185">String</span></span>|  
|<span data-ttu-id="9dd58-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9dd58-186">COLUMN_DEF</span></span>|<span data-ttu-id="9dd58-187">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-187">String</span></span>|  
|<span data-ttu-id="9dd58-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-189">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-189">Int16</span></span>|  
|<span data-ttu-id="9dd58-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9dd58-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9dd58-191">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-191">Int16</span></span>|  
|<span data-ttu-id="9dd58-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9dd58-193">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-193">Int32</span></span>|  
|<span data-ttu-id="9dd58-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-195">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-195">Int32</span></span>|  
|<span data-ttu-id="9dd58-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9dd58-196">IS_NULLABLE</span></span>|<span data-ttu-id="9dd58-197">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-197">String</span></span>|  
|<span data-ttu-id="9dd58-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9dd58-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9dd58-199">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-199">String</span></span>|  
|<span data-ttu-id="9dd58-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9dd58-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9dd58-201">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-201">String</span></span>|  
|<span data-ttu-id="9dd58-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-203">Byte</span><span class="sxs-lookup"><span data-stu-id="9dd58-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9dd58-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-204">Procedures</span></span>  
  
|<span data-ttu-id="9dd58-205">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-205">ColumnName</span></span>|<span data-ttu-id="9dd58-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="9dd58-208">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-208">String</span></span>|  
|<span data-ttu-id="9dd58-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9dd58-210">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-210">String</span></span>|  
|<span data-ttu-id="9dd58-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-212">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-212">String</span></span>|  
|<span data-ttu-id="9dd58-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-214">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-214">Int32</span></span>|  
|<span data-ttu-id="9dd58-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-216">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-216">Int32</span></span>|  
|<span data-ttu-id="9dd58-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9dd58-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9dd58-218">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-218">Int32</span></span>|  
|<span data-ttu-id="9dd58-219">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-219">REMARKS</span></span>|<span data-ttu-id="9dd58-220">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-220">String</span></span>|  
|<span data-ttu-id="9dd58-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9dd58-222">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9dd58-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9dd58-224">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-224">ColumnName</span></span>|<span data-ttu-id="9dd58-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="9dd58-227">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-227">String</span></span>|  
|<span data-ttu-id="9dd58-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9dd58-229">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-229">String</span></span>|  
|<span data-ttu-id="9dd58-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-231">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-231">String</span></span>|  
|<span data-ttu-id="9dd58-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-232">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-233">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-233">String</span></span>|  
|<span data-ttu-id="9dd58-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-234">COLUMN_TYPE</span></span>|<span data-ttu-id="9dd58-235">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-235">Int16</span></span>|  
|<span data-ttu-id="9dd58-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-236">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-237">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-237">Int16</span></span>|  
|<span data-ttu-id="9dd58-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-238">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-239">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-239">String</span></span>|  
|<span data-ttu-id="9dd58-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9dd58-240">COLUMN_SIZE</span></span>|<span data-ttu-id="9dd58-241">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-241">Int32</span></span>|  
|<span data-ttu-id="9dd58-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="9dd58-243">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-243">Int32</span></span>|  
|<span data-ttu-id="9dd58-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9dd58-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9dd58-245">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-245">Int16</span></span>|  
|<span data-ttu-id="9dd58-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9dd58-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9dd58-247">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-247">Int16</span></span>|  
|<span data-ttu-id="9dd58-248">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-248">NULLABLE</span></span>|<span data-ttu-id="9dd58-249">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-249">Int16</span></span>|  
|<span data-ttu-id="9dd58-250">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-250">REMARKS</span></span>|<span data-ttu-id="9dd58-251">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-251">String</span></span>|  
|<span data-ttu-id="9dd58-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9dd58-252">COLUMN_DEF</span></span>|<span data-ttu-id="9dd58-253">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-253">String</span></span>|  
|<span data-ttu-id="9dd58-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-255">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-255">Int16</span></span>|  
|<span data-ttu-id="9dd58-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9dd58-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9dd58-257">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-257">Int16</span></span>|  
|<span data-ttu-id="9dd58-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9dd58-259">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-259">Int32</span></span>|  
|<span data-ttu-id="9dd58-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-261">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-261">Int32</span></span>|  
|<span data-ttu-id="9dd58-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9dd58-262">IS_NULLABLE</span></span>|<span data-ttu-id="9dd58-263">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-263">String</span></span>|  
|<span data-ttu-id="9dd58-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9dd58-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9dd58-265">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-265">String</span></span>|  
|<span data-ttu-id="9dd58-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9dd58-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9dd58-267">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-267">String</span></span>|  
|<span data-ttu-id="9dd58-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-269">Byte</span><span class="sxs-lookup"><span data-stu-id="9dd58-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9dd58-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9dd58-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9dd58-271">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-271">ColumnName</span></span>|<span data-ttu-id="9dd58-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="9dd58-274">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-274">String</span></span>|  
|<span data-ttu-id="9dd58-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9dd58-276">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-276">String</span></span>|  
|<span data-ttu-id="9dd58-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-278">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-278">String</span></span>|  
|<span data-ttu-id="9dd58-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-279">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-280">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-280">String</span></span>|  
|<span data-ttu-id="9dd58-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-281">COLUMN_TYPE</span></span>|<span data-ttu-id="9dd58-282">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-282">Int16</span></span>|  
|<span data-ttu-id="9dd58-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-283">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-284">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-284">Int16</span></span>|  
|<span data-ttu-id="9dd58-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-285">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-286">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-286">String</span></span>|  
|<span data-ttu-id="9dd58-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9dd58-287">COLUMN_SIZE</span></span>|<span data-ttu-id="9dd58-288">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-288">Int32</span></span>|  
|<span data-ttu-id="9dd58-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="9dd58-290">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-290">Int32</span></span>|  
|<span data-ttu-id="9dd58-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9dd58-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9dd58-292">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-292">Int16</span></span>|  
|<span data-ttu-id="9dd58-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9dd58-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9dd58-294">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-294">Int16</span></span>|  
|<span data-ttu-id="9dd58-295">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-295">NULLABLE</span></span>|<span data-ttu-id="9dd58-296">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-296">Int16</span></span>|  
|<span data-ttu-id="9dd58-297">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-297">REMARKS</span></span>|<span data-ttu-id="9dd58-298">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-298">String</span></span>|  
|<span data-ttu-id="9dd58-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9dd58-299">COLUMN_DEF</span></span>|<span data-ttu-id="9dd58-300">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-300">String</span></span>|  
|<span data-ttu-id="9dd58-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-302">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-302">Int16</span></span>|  
|<span data-ttu-id="9dd58-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9dd58-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9dd58-304">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-304">Int16</span></span>|  
|<span data-ttu-id="9dd58-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9dd58-306">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-306">Int32</span></span>|  
|<span data-ttu-id="9dd58-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-308">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-308">Int32</span></span>|  
|<span data-ttu-id="9dd58-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9dd58-309">IS_NULLABLE</span></span>|<span data-ttu-id="9dd58-310">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-310">String</span></span>|  
|<span data-ttu-id="9dd58-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9dd58-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="9dd58-312">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-312">String</span></span>|  
|<span data-ttu-id="9dd58-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9dd58-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="9dd58-314">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-314">String</span></span>|  
|<span data-ttu-id="9dd58-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-316">Byte</span><span class="sxs-lookup"><span data-stu-id="9dd58-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="9dd58-317">Sterownik ODBC rozwiązań Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="9dd58-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="9dd58-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="9dd58-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9dd58-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="9dd58-319">Tables</span></span>  
  
-   <span data-ttu-id="9dd58-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-320">Columns</span></span>  
  
-   <span data-ttu-id="9dd58-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-321">Procedures</span></span>  
  
-   <span data-ttu-id="9dd58-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9dd58-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9dd58-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9dd58-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-324">Views</span></span>  
  
-   <span data-ttu-id="9dd58-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="9dd58-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9dd58-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-326">Tables and Views</span></span>  
  
|<span data-ttu-id="9dd58-327">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-327">ColumnName</span></span>|<span data-ttu-id="9dd58-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-330">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-330">String</span></span>|  
|<span data-ttu-id="9dd58-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-331">TABLE_OWNER</span></span>|<span data-ttu-id="9dd58-332">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-332">String</span></span>|  
|<span data-ttu-id="9dd58-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-333">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-334">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-334">String</span></span>|  
|<span data-ttu-id="9dd58-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-335">TABLE_TYPE</span></span>|<span data-ttu-id="9dd58-336">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-336">String</span></span>|  
|<span data-ttu-id="9dd58-337">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-337">REMARKS</span></span>|<span data-ttu-id="9dd58-338">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9dd58-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-339">Columns</span></span>  
  
|<span data-ttu-id="9dd58-340">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-340">ColumnName</span></span>|<span data-ttu-id="9dd58-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-343">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-343">String</span></span>|  
|<span data-ttu-id="9dd58-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-344">TABLE_OWNER</span></span>|<span data-ttu-id="9dd58-345">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-345">String</span></span>|  
|<span data-ttu-id="9dd58-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-346">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-347">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-347">String</span></span>|  
|<span data-ttu-id="9dd58-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-348">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-349">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-349">String</span></span>|  
|<span data-ttu-id="9dd58-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-350">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-351">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-351">Int16</span></span>|  
|<span data-ttu-id="9dd58-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-352">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-353">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-353">String</span></span>|  
|<span data-ttu-id="9dd58-354">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-354">PRECISION</span></span>|<span data-ttu-id="9dd58-355">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-355">Int32</span></span>|  
|<span data-ttu-id="9dd58-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-356">LENGTH</span></span>|<span data-ttu-id="9dd58-357">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-357">Int32</span></span>|  
|<span data-ttu-id="9dd58-358">SKALI</span><span class="sxs-lookup"><span data-stu-id="9dd58-358">SCALE</span></span>|<span data-ttu-id="9dd58-359">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-359">Int16</span></span>|  
|<span data-ttu-id="9dd58-360">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="9dd58-360">RADIX</span></span>|<span data-ttu-id="9dd58-361">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-361">Int16</span></span>|  
|<span data-ttu-id="9dd58-362">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-362">NULLABLE</span></span>|<span data-ttu-id="9dd58-363">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-363">Int16</span></span>|  
|<span data-ttu-id="9dd58-364">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-364">REMARKS</span></span>|<span data-ttu-id="9dd58-365">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-365">String</span></span>|  
|<span data-ttu-id="9dd58-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-367">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9dd58-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-368">Procedures</span></span>  
  
|<span data-ttu-id="9dd58-369">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-369">ColumnName</span></span>|<span data-ttu-id="9dd58-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-372">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-372">String</span></span>|  
|<span data-ttu-id="9dd58-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9dd58-374">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-374">String</span></span>|  
|<span data-ttu-id="9dd58-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-376">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-376">String</span></span>|  
|<span data-ttu-id="9dd58-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-378">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-378">Int16</span></span>|  
|<span data-ttu-id="9dd58-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-380">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-380">Int16</span></span>|  
|<span data-ttu-id="9dd58-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9dd58-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9dd58-382">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-382">Int16</span></span>|  
|<span data-ttu-id="9dd58-383">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-383">REMARKS</span></span>|<span data-ttu-id="9dd58-384">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-384">String</span></span>|  
|<span data-ttu-id="9dd58-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9dd58-386">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9dd58-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9dd58-388">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-388">ColumnName</span></span>|<span data-ttu-id="9dd58-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-391">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-391">String</span></span>|  
|<span data-ttu-id="9dd58-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9dd58-393">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-393">String</span></span>|  
|<span data-ttu-id="9dd58-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-395">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-395">String</span></span>|  
|<span data-ttu-id="9dd58-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-396">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-397">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-397">String</span></span>|  
|<span data-ttu-id="9dd58-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-398">COLUMN_TYPE</span></span>|<span data-ttu-id="9dd58-399">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-399">Int16</span></span>|  
|<span data-ttu-id="9dd58-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-400">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-401">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-401">Int16</span></span>|  
|<span data-ttu-id="9dd58-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-402">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-403">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-403">String</span></span>|  
|<span data-ttu-id="9dd58-404">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-404">PRECISION</span></span>|<span data-ttu-id="9dd58-405">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-405">Int32</span></span>|  
|<span data-ttu-id="9dd58-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-406">LENGTH</span></span>|<span data-ttu-id="9dd58-407">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-407">Int32</span></span>|  
|<span data-ttu-id="9dd58-408">SKALI</span><span class="sxs-lookup"><span data-stu-id="9dd58-408">SCALE</span></span>|<span data-ttu-id="9dd58-409">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-409">Int16</span></span>|  
|<span data-ttu-id="9dd58-410">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="9dd58-410">RADIX</span></span>|<span data-ttu-id="9dd58-411">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-411">Int16</span></span>|  
|<span data-ttu-id="9dd58-412">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-412">NULLABLE</span></span>|<span data-ttu-id="9dd58-413">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-413">Int16</span></span>|  
|<span data-ttu-id="9dd58-414">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-414">REMARKS</span></span>|<span data-ttu-id="9dd58-415">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-415">String</span></span>|  
|<span data-ttu-id="9dd58-416">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="9dd58-416">OVERLOAD</span></span>|<span data-ttu-id="9dd58-417">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-417">Int32</span></span>|  
|<span data-ttu-id="9dd58-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-419">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="9dd58-420">Sterownik ODBC dla programu Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="9dd58-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="9dd58-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="9dd58-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="9dd58-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="9dd58-422">Tables</span></span>  
  
-   <span data-ttu-id="9dd58-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="9dd58-423">Indexes</span></span>  
  
-   <span data-ttu-id="9dd58-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-424">Columns</span></span>  
  
-   <span data-ttu-id="9dd58-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-425">Procedures</span></span>  
  
-   <span data-ttu-id="9dd58-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="9dd58-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9dd58-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="9dd58-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="9dd58-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="9dd58-429">Tables and Views</span></span>  
  
|<span data-ttu-id="9dd58-430">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-430">ColumnName</span></span>|<span data-ttu-id="9dd58-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-433">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-433">String</span></span>|  
|<span data-ttu-id="9dd58-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-434">TABLE_OWNER</span></span>|<span data-ttu-id="9dd58-435">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-435">String</span></span>|  
|<span data-ttu-id="9dd58-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-436">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-437">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-437">String</span></span>|  
|<span data-ttu-id="9dd58-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-438">TABLE_TYPE</span></span>|<span data-ttu-id="9dd58-439">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-439">String</span></span>|  
|<span data-ttu-id="9dd58-440">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-440">REMARKS</span></span>|<span data-ttu-id="9dd58-441">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9dd58-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9dd58-442">Columns</span></span>  
  
|<span data-ttu-id="9dd58-443">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-443">ColumnName</span></span>|<span data-ttu-id="9dd58-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-446">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-446">String</span></span>|  
|<span data-ttu-id="9dd58-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-447">TABLE_OWNER</span></span>|<span data-ttu-id="9dd58-448">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-448">String</span></span>|  
|<span data-ttu-id="9dd58-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-449">TABLE_NAME</span></span>|<span data-ttu-id="9dd58-450">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-450">String</span></span>|  
|<span data-ttu-id="9dd58-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-451">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-452">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-452">String</span></span>|  
|<span data-ttu-id="9dd58-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-453">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-454">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-454">Int16</span></span>|  
|<span data-ttu-id="9dd58-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-455">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-456">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-456">String</span></span>|  
|<span data-ttu-id="9dd58-457">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-457">PRECISION</span></span>|<span data-ttu-id="9dd58-458">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-458">Int32</span></span>|  
|<span data-ttu-id="9dd58-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-459">LENGTH</span></span>|<span data-ttu-id="9dd58-460">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-460">Int32</span></span>|  
|<span data-ttu-id="9dd58-461">SKALI</span><span class="sxs-lookup"><span data-stu-id="9dd58-461">SCALE</span></span>|<span data-ttu-id="9dd58-462">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-462">Int16</span></span>|  
|<span data-ttu-id="9dd58-463">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="9dd58-463">RADIX</span></span>|<span data-ttu-id="9dd58-464">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-464">Int16</span></span>|  
|<span data-ttu-id="9dd58-465">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-465">NULLABLE</span></span>|<span data-ttu-id="9dd58-466">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-466">Int16</span></span>|  
|<span data-ttu-id="9dd58-467">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-467">REMARKS</span></span>|<span data-ttu-id="9dd58-468">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-468">String</span></span>|  
|<span data-ttu-id="9dd58-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-470">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9dd58-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="9dd58-471">Procedures</span></span>  
  
|<span data-ttu-id="9dd58-472">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-472">ColumnName</span></span>|<span data-ttu-id="9dd58-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-475">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-475">String</span></span>|  
|<span data-ttu-id="9dd58-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9dd58-477">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-477">String</span></span>|  
|<span data-ttu-id="9dd58-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-479">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-479">String</span></span>|  
|<span data-ttu-id="9dd58-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-481">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-481">Int16</span></span>|  
|<span data-ttu-id="9dd58-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="9dd58-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="9dd58-483">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-483">Int16</span></span>|  
|<span data-ttu-id="9dd58-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="9dd58-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="9dd58-485">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-485">Int16</span></span>|  
|<span data-ttu-id="9dd58-486">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-486">REMARKS</span></span>|<span data-ttu-id="9dd58-487">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-487">String</span></span>|  
|<span data-ttu-id="9dd58-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="9dd58-489">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="9dd58-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="9dd58-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="9dd58-491">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-491">ColumnName</span></span>|<span data-ttu-id="9dd58-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="9dd58-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="9dd58-494">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-494">String</span></span>|  
|<span data-ttu-id="9dd58-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="9dd58-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="9dd58-496">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-496">String</span></span>|  
|<span data-ttu-id="9dd58-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-498">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-498">String</span></span>|  
|<span data-ttu-id="9dd58-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-499">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-500">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-500">String</span></span>|  
|<span data-ttu-id="9dd58-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-501">COLUMN_TYPE</span></span>|<span data-ttu-id="9dd58-502">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-502">Int16</span></span>|  
|<span data-ttu-id="9dd58-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-503">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-504">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-504">Int16</span></span>|  
|<span data-ttu-id="9dd58-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-505">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-506">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-506">String</span></span>|  
|<span data-ttu-id="9dd58-507">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-507">PRECISION</span></span>|<span data-ttu-id="9dd58-508">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-508">Int32</span></span>|  
|<span data-ttu-id="9dd58-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="9dd58-509">LENGTH</span></span>|<span data-ttu-id="9dd58-510">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-510">Int32</span></span>|  
|<span data-ttu-id="9dd58-511">SKALI</span><span class="sxs-lookup"><span data-stu-id="9dd58-511">SCALE</span></span>|<span data-ttu-id="9dd58-512">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-512">Int16</span></span>|  
|<span data-ttu-id="9dd58-513">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="9dd58-513">RADIX</span></span>|<span data-ttu-id="9dd58-514">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-514">Int16</span></span>|  
|<span data-ttu-id="9dd58-515">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-515">NULLABLE</span></span>|<span data-ttu-id="9dd58-516">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-516">Int16</span></span>|  
|<span data-ttu-id="9dd58-517">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-517">REMARKS</span></span>|<span data-ttu-id="9dd58-518">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-518">String</span></span>|  
|<span data-ttu-id="9dd58-519">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="9dd58-519">OVERLOAD</span></span>|<span data-ttu-id="9dd58-520">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-520">Int32</span></span>|  
|<span data-ttu-id="9dd58-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-522">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9dd58-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9dd58-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9dd58-524">Element columnName</span><span class="sxs-lookup"><span data-stu-id="9dd58-524">ColumnName</span></span>|<span data-ttu-id="9dd58-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9dd58-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="9dd58-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="9dd58-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="9dd58-527">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-527">String</span></span>|  
|<span data-ttu-id="9dd58-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="9dd58-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="9dd58-529">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-529">String</span></span>|  
|<span data-ttu-id="9dd58-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="9dd58-531">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-531">String</span></span>|  
|<span data-ttu-id="9dd58-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-532">COLUMN_NAME</span></span>|<span data-ttu-id="9dd58-533">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-533">String</span></span>|  
|<span data-ttu-id="9dd58-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-534">COLUMN_TYPE</span></span>|<span data-ttu-id="9dd58-535">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-535">Int16</span></span>|  
|<span data-ttu-id="9dd58-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-536">DATA_TYPE</span></span>|<span data-ttu-id="9dd58-537">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-537">Int16</span></span>|  
|<span data-ttu-id="9dd58-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="9dd58-538">TYPE_NAME</span></span>|<span data-ttu-id="9dd58-539">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-539">String</span></span>|  
|<span data-ttu-id="9dd58-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="9dd58-540">COLUMN_SIZE</span></span>|<span data-ttu-id="9dd58-541">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-541">Int32</span></span>|  
|<span data-ttu-id="9dd58-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="9dd58-543">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-543">Int32</span></span>|  
|<span data-ttu-id="9dd58-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="9dd58-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="9dd58-545">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-545">Int16</span></span>|  
|<span data-ttu-id="9dd58-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="9dd58-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="9dd58-547">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-547">Int16</span></span>|  
|<span data-ttu-id="9dd58-548">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="9dd58-548">NULLABLE</span></span>|<span data-ttu-id="9dd58-549">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-549">Int16</span></span>|  
|<span data-ttu-id="9dd58-550">UWAGI</span><span class="sxs-lookup"><span data-stu-id="9dd58-550">REMARKS</span></span>|<span data-ttu-id="9dd58-551">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-551">String</span></span>|  
|<span data-ttu-id="9dd58-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="9dd58-552">COLUMN_DEF</span></span>|<span data-ttu-id="9dd58-553">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-553">String</span></span>|  
|<span data-ttu-id="9dd58-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="9dd58-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="9dd58-555">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-555">Int16</span></span>|  
|<span data-ttu-id="9dd58-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="9dd58-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="9dd58-557">Int16</span><span class="sxs-lookup"><span data-stu-id="9dd58-557">Int16</span></span>|  
|<span data-ttu-id="9dd58-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="9dd58-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="9dd58-559">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-559">Int32</span></span>|  
|<span data-ttu-id="9dd58-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="9dd58-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="9dd58-561">Int32</span><span class="sxs-lookup"><span data-stu-id="9dd58-561">Int32</span></span>|  
|<span data-ttu-id="9dd58-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="9dd58-562">IS_NULLABLE</span></span>|<span data-ttu-id="9dd58-563">String</span><span class="sxs-lookup"><span data-stu-id="9dd58-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9dd58-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dd58-564">See Also</span></span>  
 [<span data-ttu-id="9dd58-565">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9dd58-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
