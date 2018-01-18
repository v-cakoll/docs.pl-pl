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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="b268e-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="b268e-102">ODBC Schema Collections</span></span>
<span data-ttu-id="b268e-103">W tej sekcji omówiono obsługi kolekcji schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="b268e-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="b268e-104">Sterownik ODBC programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="b268e-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="b268e-105">Sterownik ODBC programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b268e-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b268e-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="b268e-106">Tables</span></span>  
  
-   <span data-ttu-id="b268e-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b268e-107">Indexes</span></span>  
  
-   <span data-ttu-id="b268e-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-108">Columns</span></span>  
  
-   <span data-ttu-id="b268e-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-109">Procedures</span></span>  
  
-   <span data-ttu-id="b268e-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b268e-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b268e-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b268e-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b268e-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-113">Tables and Views</span></span>  
  
|<span data-ttu-id="b268e-114">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-114">ColumnName</span></span>|<span data-ttu-id="b268e-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-116">TABLE_CAT</span></span>|<span data-ttu-id="b268e-117">String</span><span class="sxs-lookup"><span data-stu-id="b268e-117">String</span></span>|  
|<span data-ttu-id="b268e-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-118">TABLE_SCHEM</span></span>|<span data-ttu-id="b268e-119">String</span><span class="sxs-lookup"><span data-stu-id="b268e-119">String</span></span>|  
|<span data-ttu-id="b268e-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-120">TABLE_NAME</span></span>|<span data-ttu-id="b268e-121">String</span><span class="sxs-lookup"><span data-stu-id="b268e-121">String</span></span>|  
|<span data-ttu-id="b268e-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-122">TABLE_TYPE</span></span>|<span data-ttu-id="b268e-123">String</span><span class="sxs-lookup"><span data-stu-id="b268e-123">String</span></span>|  
|<span data-ttu-id="b268e-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-124">REMARKS</span></span>|<span data-ttu-id="b268e-125">String</span><span class="sxs-lookup"><span data-stu-id="b268e-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b268e-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b268e-126">Indexes</span></span>  
  
|<span data-ttu-id="b268e-127">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-127">ColumnName</span></span>|<span data-ttu-id="b268e-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-129">TABLE_CAT</span></span>|<span data-ttu-id="b268e-130">String</span><span class="sxs-lookup"><span data-stu-id="b268e-130">String</span></span>|  
|<span data-ttu-id="b268e-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-131">TABLE_SCHEM</span></span>|<span data-ttu-id="b268e-132">String</span><span class="sxs-lookup"><span data-stu-id="b268e-132">String</span></span>|  
|<span data-ttu-id="b268e-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-133">TABLE_NAME</span></span>|<span data-ttu-id="b268e-134">String</span><span class="sxs-lookup"><span data-stu-id="b268e-134">String</span></span>|  
|<span data-ttu-id="b268e-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b268e-135">NON_UNIQUE</span></span>|<span data-ttu-id="b268e-136">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-136">Int16</span></span>|  
|<span data-ttu-id="b268e-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="b268e-138">String</span><span class="sxs-lookup"><span data-stu-id="b268e-138">String</span></span>|  
|<span data-ttu-id="b268e-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-139">INDEX_NAME</span></span>|<span data-ttu-id="b268e-140">String</span><span class="sxs-lookup"><span data-stu-id="b268e-140">String</span></span>|  
|<span data-ttu-id="b268e-141">TYP</span><span class="sxs-lookup"><span data-stu-id="b268e-141">TYPE</span></span>|<span data-ttu-id="b268e-142">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-142">Int16</span></span>|  
|<span data-ttu-id="b268e-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-144">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-144">Int16</span></span>|  
|<span data-ttu-id="b268e-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-145">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-146">String</span><span class="sxs-lookup"><span data-stu-id="b268e-146">String</span></span>|  
|<span data-ttu-id="b268e-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="b268e-147">ASC_OR_DESC</span></span>|<span data-ttu-id="b268e-148">String</span><span class="sxs-lookup"><span data-stu-id="b268e-148">String</span></span>|  
|<span data-ttu-id="b268e-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="b268e-149">CARDINATLITY</span></span>|<span data-ttu-id="b268e-150">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-150">Int32</span></span>|  
|<span data-ttu-id="b268e-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="b268e-151">PAGES</span></span>|<span data-ttu-id="b268e-152">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-152">Int32</span></span>|  
|<span data-ttu-id="b268e-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b268e-153">FILTER_CONDITION</span></span>|<span data-ttu-id="b268e-154">String</span><span class="sxs-lookup"><span data-stu-id="b268e-154">String</span></span>|  
|<span data-ttu-id="b268e-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b268e-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b268e-156">String</span><span class="sxs-lookup"><span data-stu-id="b268e-156">String</span></span>|  
|<span data-ttu-id="b268e-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="b268e-158">Byte</span><span class="sxs-lookup"><span data-stu-id="b268e-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b268e-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-159">Columns</span></span>  
  
|<span data-ttu-id="b268e-160">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-160">ColumnName</span></span>|<span data-ttu-id="b268e-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-162">TABLE_CAT</span></span>|<span data-ttu-id="b268e-163">String</span><span class="sxs-lookup"><span data-stu-id="b268e-163">String</span></span>|  
|<span data-ttu-id="b268e-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-164">TABLE_SCHEM</span></span>|<span data-ttu-id="b268e-165">String</span><span class="sxs-lookup"><span data-stu-id="b268e-165">String</span></span>|  
|<span data-ttu-id="b268e-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-166">TABLE_NAME</span></span>|<span data-ttu-id="b268e-167">String</span><span class="sxs-lookup"><span data-stu-id="b268e-167">String</span></span>|  
|<span data-ttu-id="b268e-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-168">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-169">String</span><span class="sxs-lookup"><span data-stu-id="b268e-169">String</span></span>|  
|<span data-ttu-id="b268e-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-170">DATA_TYPE</span></span>|<span data-ttu-id="b268e-171">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-171">Int16</span></span>|  
|<span data-ttu-id="b268e-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-172">TYPE_NAME</span></span>|<span data-ttu-id="b268e-173">String</span><span class="sxs-lookup"><span data-stu-id="b268e-173">String</span></span>|  
|<span data-ttu-id="b268e-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b268e-174">COLUMN_SIZE</span></span>|<span data-ttu-id="b268e-175">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-175">Int32</span></span>|  
|<span data-ttu-id="b268e-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="b268e-177">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-177">Int32</span></span>|  
|<span data-ttu-id="b268e-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b268e-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b268e-179">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-179">Int16</span></span>|  
|<span data-ttu-id="b268e-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b268e-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b268e-181">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-181">Int16</span></span>|  
|<span data-ttu-id="b268e-182">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-182">NULLABLE</span></span>|<span data-ttu-id="b268e-183">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-183">Int16</span></span>|  
|<span data-ttu-id="b268e-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-184">REMARKS</span></span>|<span data-ttu-id="b268e-185">String</span><span class="sxs-lookup"><span data-stu-id="b268e-185">String</span></span>|  
|<span data-ttu-id="b268e-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b268e-186">COLUMN_DEF</span></span>|<span data-ttu-id="b268e-187">String</span><span class="sxs-lookup"><span data-stu-id="b268e-187">String</span></span>|  
|<span data-ttu-id="b268e-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b268e-189">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-189">Int16</span></span>|  
|<span data-ttu-id="b268e-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b268e-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b268e-191">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-191">Int16</span></span>|  
|<span data-ttu-id="b268e-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b268e-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-193">Int32</span></span>|  
|<span data-ttu-id="b268e-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-195">Int32</span></span>|  
|<span data-ttu-id="b268e-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b268e-196">IS_NULLABLE</span></span>|<span data-ttu-id="b268e-197">String</span><span class="sxs-lookup"><span data-stu-id="b268e-197">String</span></span>|  
|<span data-ttu-id="b268e-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b268e-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b268e-199">String</span><span class="sxs-lookup"><span data-stu-id="b268e-199">String</span></span>|  
|<span data-ttu-id="b268e-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b268e-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b268e-201">String</span><span class="sxs-lookup"><span data-stu-id="b268e-201">String</span></span>|  
|<span data-ttu-id="b268e-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="b268e-203">Byte</span><span class="sxs-lookup"><span data-stu-id="b268e-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b268e-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-204">Procedures</span></span>  
  
|<span data-ttu-id="b268e-205">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-205">ColumnName</span></span>|<span data-ttu-id="b268e-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="b268e-208">String</span><span class="sxs-lookup"><span data-stu-id="b268e-208">String</span></span>|  
|<span data-ttu-id="b268e-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b268e-210">String</span><span class="sxs-lookup"><span data-stu-id="b268e-210">String</span></span>|  
|<span data-ttu-id="b268e-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-212">String</span><span class="sxs-lookup"><span data-stu-id="b268e-212">String</span></span>|  
|<span data-ttu-id="b268e-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b268e-214">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-214">Int32</span></span>|  
|<span data-ttu-id="b268e-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b268e-216">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-216">Int32</span></span>|  
|<span data-ttu-id="b268e-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b268e-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b268e-218">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-218">Int32</span></span>|  
|<span data-ttu-id="b268e-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-219">REMARKS</span></span>|<span data-ttu-id="b268e-220">String</span><span class="sxs-lookup"><span data-stu-id="b268e-220">String</span></span>|  
|<span data-ttu-id="b268e-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b268e-222">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b268e-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b268e-224">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-224">ColumnName</span></span>|<span data-ttu-id="b268e-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="b268e-227">String</span><span class="sxs-lookup"><span data-stu-id="b268e-227">String</span></span>|  
|<span data-ttu-id="b268e-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b268e-229">String</span><span class="sxs-lookup"><span data-stu-id="b268e-229">String</span></span>|  
|<span data-ttu-id="b268e-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-231">String</span><span class="sxs-lookup"><span data-stu-id="b268e-231">String</span></span>|  
|<span data-ttu-id="b268e-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-232">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-233">String</span><span class="sxs-lookup"><span data-stu-id="b268e-233">String</span></span>|  
|<span data-ttu-id="b268e-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-234">COLUMN_TYPE</span></span>|<span data-ttu-id="b268e-235">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-235">Int16</span></span>|  
|<span data-ttu-id="b268e-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-236">DATA_TYPE</span></span>|<span data-ttu-id="b268e-237">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-237">Int16</span></span>|  
|<span data-ttu-id="b268e-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-238">TYPE_NAME</span></span>|<span data-ttu-id="b268e-239">String</span><span class="sxs-lookup"><span data-stu-id="b268e-239">String</span></span>|  
|<span data-ttu-id="b268e-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b268e-240">COLUMN_SIZE</span></span>|<span data-ttu-id="b268e-241">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-241">Int32</span></span>|  
|<span data-ttu-id="b268e-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="b268e-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-243">Int32</span></span>|  
|<span data-ttu-id="b268e-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b268e-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b268e-245">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-245">Int16</span></span>|  
|<span data-ttu-id="b268e-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b268e-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b268e-247">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-247">Int16</span></span>|  
|<span data-ttu-id="b268e-248">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-248">NULLABLE</span></span>|<span data-ttu-id="b268e-249">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-249">Int16</span></span>|  
|<span data-ttu-id="b268e-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-250">REMARKS</span></span>|<span data-ttu-id="b268e-251">String</span><span class="sxs-lookup"><span data-stu-id="b268e-251">String</span></span>|  
|<span data-ttu-id="b268e-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b268e-252">COLUMN_DEF</span></span>|<span data-ttu-id="b268e-253">String</span><span class="sxs-lookup"><span data-stu-id="b268e-253">String</span></span>|  
|<span data-ttu-id="b268e-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b268e-255">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-255">Int16</span></span>|  
|<span data-ttu-id="b268e-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b268e-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b268e-257">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-257">Int16</span></span>|  
|<span data-ttu-id="b268e-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b268e-259">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-259">Int32</span></span>|  
|<span data-ttu-id="b268e-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-261">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-261">Int32</span></span>|  
|<span data-ttu-id="b268e-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b268e-262">IS_NULLABLE</span></span>|<span data-ttu-id="b268e-263">String</span><span class="sxs-lookup"><span data-stu-id="b268e-263">String</span></span>|  
|<span data-ttu-id="b268e-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b268e-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b268e-265">String</span><span class="sxs-lookup"><span data-stu-id="b268e-265">String</span></span>|  
|<span data-ttu-id="b268e-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b268e-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b268e-267">String</span><span class="sxs-lookup"><span data-stu-id="b268e-267">String</span></span>|  
|<span data-ttu-id="b268e-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="b268e-269">Byte</span><span class="sxs-lookup"><span data-stu-id="b268e-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b268e-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b268e-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b268e-271">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-271">ColumnName</span></span>|<span data-ttu-id="b268e-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="b268e-274">String</span><span class="sxs-lookup"><span data-stu-id="b268e-274">String</span></span>|  
|<span data-ttu-id="b268e-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b268e-276">String</span><span class="sxs-lookup"><span data-stu-id="b268e-276">String</span></span>|  
|<span data-ttu-id="b268e-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-278">String</span><span class="sxs-lookup"><span data-stu-id="b268e-278">String</span></span>|  
|<span data-ttu-id="b268e-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-279">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-280">String</span><span class="sxs-lookup"><span data-stu-id="b268e-280">String</span></span>|  
|<span data-ttu-id="b268e-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-281">COLUMN_TYPE</span></span>|<span data-ttu-id="b268e-282">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-282">Int16</span></span>|  
|<span data-ttu-id="b268e-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-283">DATA_TYPE</span></span>|<span data-ttu-id="b268e-284">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-284">Int16</span></span>|  
|<span data-ttu-id="b268e-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-285">TYPE_NAME</span></span>|<span data-ttu-id="b268e-286">String</span><span class="sxs-lookup"><span data-stu-id="b268e-286">String</span></span>|  
|<span data-ttu-id="b268e-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b268e-287">COLUMN_SIZE</span></span>|<span data-ttu-id="b268e-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-288">Int32</span></span>|  
|<span data-ttu-id="b268e-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="b268e-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-290">Int32</span></span>|  
|<span data-ttu-id="b268e-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b268e-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b268e-292">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-292">Int16</span></span>|  
|<span data-ttu-id="b268e-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b268e-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b268e-294">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-294">Int16</span></span>|  
|<span data-ttu-id="b268e-295">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-295">NULLABLE</span></span>|<span data-ttu-id="b268e-296">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-296">Int16</span></span>|  
|<span data-ttu-id="b268e-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-297">REMARKS</span></span>|<span data-ttu-id="b268e-298">String</span><span class="sxs-lookup"><span data-stu-id="b268e-298">String</span></span>|  
|<span data-ttu-id="b268e-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b268e-299">COLUMN_DEF</span></span>|<span data-ttu-id="b268e-300">String</span><span class="sxs-lookup"><span data-stu-id="b268e-300">String</span></span>|  
|<span data-ttu-id="b268e-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b268e-302">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-302">Int16</span></span>|  
|<span data-ttu-id="b268e-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b268e-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b268e-304">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-304">Int16</span></span>|  
|<span data-ttu-id="b268e-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b268e-306">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-306">Int32</span></span>|  
|<span data-ttu-id="b268e-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-308">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-308">Int32</span></span>|  
|<span data-ttu-id="b268e-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b268e-309">IS_NULLABLE</span></span>|<span data-ttu-id="b268e-310">String</span><span class="sxs-lookup"><span data-stu-id="b268e-310">String</span></span>|  
|<span data-ttu-id="b268e-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b268e-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b268e-312">String</span><span class="sxs-lookup"><span data-stu-id="b268e-312">String</span></span>|  
|<span data-ttu-id="b268e-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b268e-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b268e-314">String</span><span class="sxs-lookup"><span data-stu-id="b268e-314">String</span></span>|  
|<span data-ttu-id="b268e-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="b268e-316">Byte</span><span class="sxs-lookup"><span data-stu-id="b268e-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="b268e-317">Sterownik ODBC rozwiązań Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="b268e-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="b268e-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b268e-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b268e-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="b268e-319">Tables</span></span>  
  
-   <span data-ttu-id="b268e-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-320">Columns</span></span>  
  
-   <span data-ttu-id="b268e-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-321">Procedures</span></span>  
  
-   <span data-ttu-id="b268e-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b268e-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b268e-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b268e-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-324">Views</span></span>  
  
-   <span data-ttu-id="b268e-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b268e-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b268e-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-326">Tables and Views</span></span>  
  
|<span data-ttu-id="b268e-327">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-327">ColumnName</span></span>|<span data-ttu-id="b268e-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b268e-330">String</span><span class="sxs-lookup"><span data-stu-id="b268e-330">String</span></span>|  
|<span data-ttu-id="b268e-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-331">TABLE_OWNER</span></span>|<span data-ttu-id="b268e-332">String</span><span class="sxs-lookup"><span data-stu-id="b268e-332">String</span></span>|  
|<span data-ttu-id="b268e-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-333">TABLE_NAME</span></span>|<span data-ttu-id="b268e-334">String</span><span class="sxs-lookup"><span data-stu-id="b268e-334">String</span></span>|  
|<span data-ttu-id="b268e-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-335">TABLE_TYPE</span></span>|<span data-ttu-id="b268e-336">String</span><span class="sxs-lookup"><span data-stu-id="b268e-336">String</span></span>|  
|<span data-ttu-id="b268e-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-337">REMARKS</span></span>|<span data-ttu-id="b268e-338">String</span><span class="sxs-lookup"><span data-stu-id="b268e-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b268e-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-339">Columns</span></span>  
  
|<span data-ttu-id="b268e-340">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-340">ColumnName</span></span>|<span data-ttu-id="b268e-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b268e-343">String</span><span class="sxs-lookup"><span data-stu-id="b268e-343">String</span></span>|  
|<span data-ttu-id="b268e-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-344">TABLE_OWNER</span></span>|<span data-ttu-id="b268e-345">String</span><span class="sxs-lookup"><span data-stu-id="b268e-345">String</span></span>|  
|<span data-ttu-id="b268e-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-346">TABLE_NAME</span></span>|<span data-ttu-id="b268e-347">String</span><span class="sxs-lookup"><span data-stu-id="b268e-347">String</span></span>|  
|<span data-ttu-id="b268e-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-348">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-349">String</span><span class="sxs-lookup"><span data-stu-id="b268e-349">String</span></span>|  
|<span data-ttu-id="b268e-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-350">DATA_TYPE</span></span>|<span data-ttu-id="b268e-351">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-351">Int16</span></span>|  
|<span data-ttu-id="b268e-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-352">TYPE_NAME</span></span>|<span data-ttu-id="b268e-353">String</span><span class="sxs-lookup"><span data-stu-id="b268e-353">String</span></span>|  
|<span data-ttu-id="b268e-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b268e-354">PRECISION</span></span>|<span data-ttu-id="b268e-355">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-355">Int32</span></span>|  
|<span data-ttu-id="b268e-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b268e-356">LENGTH</span></span>|<span data-ttu-id="b268e-357">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-357">Int32</span></span>|  
|<span data-ttu-id="b268e-358">SKALI</span><span class="sxs-lookup"><span data-stu-id="b268e-358">SCALE</span></span>|<span data-ttu-id="b268e-359">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-359">Int16</span></span>|  
|<span data-ttu-id="b268e-360">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b268e-360">RADIX</span></span>|<span data-ttu-id="b268e-361">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-361">Int16</span></span>|  
|<span data-ttu-id="b268e-362">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-362">NULLABLE</span></span>|<span data-ttu-id="b268e-363">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-363">Int16</span></span>|  
|<span data-ttu-id="b268e-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-364">REMARKS</span></span>|<span data-ttu-id="b268e-365">String</span><span class="sxs-lookup"><span data-stu-id="b268e-365">String</span></span>|  
|<span data-ttu-id="b268e-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-367">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b268e-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-368">Procedures</span></span>  
  
|<span data-ttu-id="b268e-369">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-369">ColumnName</span></span>|<span data-ttu-id="b268e-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b268e-372">String</span><span class="sxs-lookup"><span data-stu-id="b268e-372">String</span></span>|  
|<span data-ttu-id="b268e-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b268e-374">String</span><span class="sxs-lookup"><span data-stu-id="b268e-374">String</span></span>|  
|<span data-ttu-id="b268e-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-376">String</span><span class="sxs-lookup"><span data-stu-id="b268e-376">String</span></span>|  
|<span data-ttu-id="b268e-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b268e-378">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-378">Int16</span></span>|  
|<span data-ttu-id="b268e-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b268e-380">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-380">Int16</span></span>|  
|<span data-ttu-id="b268e-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b268e-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b268e-382">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-382">Int16</span></span>|  
|<span data-ttu-id="b268e-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-383">REMARKS</span></span>|<span data-ttu-id="b268e-384">String</span><span class="sxs-lookup"><span data-stu-id="b268e-384">String</span></span>|  
|<span data-ttu-id="b268e-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b268e-386">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b268e-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b268e-388">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-388">ColumnName</span></span>|<span data-ttu-id="b268e-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b268e-391">String</span><span class="sxs-lookup"><span data-stu-id="b268e-391">String</span></span>|  
|<span data-ttu-id="b268e-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b268e-393">String</span><span class="sxs-lookup"><span data-stu-id="b268e-393">String</span></span>|  
|<span data-ttu-id="b268e-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-395">String</span><span class="sxs-lookup"><span data-stu-id="b268e-395">String</span></span>|  
|<span data-ttu-id="b268e-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-396">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-397">String</span><span class="sxs-lookup"><span data-stu-id="b268e-397">String</span></span>|  
|<span data-ttu-id="b268e-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-398">COLUMN_TYPE</span></span>|<span data-ttu-id="b268e-399">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-399">Int16</span></span>|  
|<span data-ttu-id="b268e-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-400">DATA_TYPE</span></span>|<span data-ttu-id="b268e-401">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-401">Int16</span></span>|  
|<span data-ttu-id="b268e-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-402">TYPE_NAME</span></span>|<span data-ttu-id="b268e-403">String</span><span class="sxs-lookup"><span data-stu-id="b268e-403">String</span></span>|  
|<span data-ttu-id="b268e-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b268e-404">PRECISION</span></span>|<span data-ttu-id="b268e-405">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-405">Int32</span></span>|  
|<span data-ttu-id="b268e-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b268e-406">LENGTH</span></span>|<span data-ttu-id="b268e-407">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-407">Int32</span></span>|  
|<span data-ttu-id="b268e-408">SKALI</span><span class="sxs-lookup"><span data-stu-id="b268e-408">SCALE</span></span>|<span data-ttu-id="b268e-409">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-409">Int16</span></span>|  
|<span data-ttu-id="b268e-410">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b268e-410">RADIX</span></span>|<span data-ttu-id="b268e-411">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-411">Int16</span></span>|  
|<span data-ttu-id="b268e-412">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-412">NULLABLE</span></span>|<span data-ttu-id="b268e-413">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-413">Int16</span></span>|  
|<span data-ttu-id="b268e-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-414">REMARKS</span></span>|<span data-ttu-id="b268e-415">String</span><span class="sxs-lookup"><span data-stu-id="b268e-415">String</span></span>|  
|<span data-ttu-id="b268e-416">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="b268e-416">OVERLOAD</span></span>|<span data-ttu-id="b268e-417">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-417">Int32</span></span>|  
|<span data-ttu-id="b268e-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-419">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="b268e-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="b268e-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="b268e-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b268e-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b268e-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="b268e-422">Tables</span></span>  
  
-   <span data-ttu-id="b268e-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b268e-423">Indexes</span></span>  
  
-   <span data-ttu-id="b268e-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-424">Columns</span></span>  
  
-   <span data-ttu-id="b268e-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-425">Procedures</span></span>  
  
-   <span data-ttu-id="b268e-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b268e-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b268e-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b268e-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b268e-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="b268e-429">Tables and Views</span></span>  
  
|<span data-ttu-id="b268e-430">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-430">ColumnName</span></span>|<span data-ttu-id="b268e-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b268e-433">String</span><span class="sxs-lookup"><span data-stu-id="b268e-433">String</span></span>|  
|<span data-ttu-id="b268e-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-434">TABLE_OWNER</span></span>|<span data-ttu-id="b268e-435">String</span><span class="sxs-lookup"><span data-stu-id="b268e-435">String</span></span>|  
|<span data-ttu-id="b268e-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-436">TABLE_NAME</span></span>|<span data-ttu-id="b268e-437">String</span><span class="sxs-lookup"><span data-stu-id="b268e-437">String</span></span>|  
|<span data-ttu-id="b268e-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-438">TABLE_TYPE</span></span>|<span data-ttu-id="b268e-439">String</span><span class="sxs-lookup"><span data-stu-id="b268e-439">String</span></span>|  
|<span data-ttu-id="b268e-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-440">REMARKS</span></span>|<span data-ttu-id="b268e-441">String</span><span class="sxs-lookup"><span data-stu-id="b268e-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b268e-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b268e-442">Columns</span></span>  
  
|<span data-ttu-id="b268e-443">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-443">ColumnName</span></span>|<span data-ttu-id="b268e-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b268e-446">String</span><span class="sxs-lookup"><span data-stu-id="b268e-446">String</span></span>|  
|<span data-ttu-id="b268e-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-447">TABLE_OWNER</span></span>|<span data-ttu-id="b268e-448">String</span><span class="sxs-lookup"><span data-stu-id="b268e-448">String</span></span>|  
|<span data-ttu-id="b268e-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-449">TABLE_NAME</span></span>|<span data-ttu-id="b268e-450">String</span><span class="sxs-lookup"><span data-stu-id="b268e-450">String</span></span>|  
|<span data-ttu-id="b268e-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-451">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-452">String</span><span class="sxs-lookup"><span data-stu-id="b268e-452">String</span></span>|  
|<span data-ttu-id="b268e-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-453">DATA_TYPE</span></span>|<span data-ttu-id="b268e-454">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-454">Int16</span></span>|  
|<span data-ttu-id="b268e-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-455">TYPE_NAME</span></span>|<span data-ttu-id="b268e-456">String</span><span class="sxs-lookup"><span data-stu-id="b268e-456">String</span></span>|  
|<span data-ttu-id="b268e-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b268e-457">PRECISION</span></span>|<span data-ttu-id="b268e-458">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-458">Int32</span></span>|  
|<span data-ttu-id="b268e-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b268e-459">LENGTH</span></span>|<span data-ttu-id="b268e-460">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-460">Int32</span></span>|  
|<span data-ttu-id="b268e-461">SKALI</span><span class="sxs-lookup"><span data-stu-id="b268e-461">SCALE</span></span>|<span data-ttu-id="b268e-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-462">Int16</span></span>|  
|<span data-ttu-id="b268e-463">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b268e-463">RADIX</span></span>|<span data-ttu-id="b268e-464">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-464">Int16</span></span>|  
|<span data-ttu-id="b268e-465">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-465">NULLABLE</span></span>|<span data-ttu-id="b268e-466">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-466">Int16</span></span>|  
|<span data-ttu-id="b268e-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-467">REMARKS</span></span>|<span data-ttu-id="b268e-468">String</span><span class="sxs-lookup"><span data-stu-id="b268e-468">String</span></span>|  
|<span data-ttu-id="b268e-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-470">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b268e-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="b268e-471">Procedures</span></span>  
  
|<span data-ttu-id="b268e-472">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-472">ColumnName</span></span>|<span data-ttu-id="b268e-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b268e-475">String</span><span class="sxs-lookup"><span data-stu-id="b268e-475">String</span></span>|  
|<span data-ttu-id="b268e-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b268e-477">String</span><span class="sxs-lookup"><span data-stu-id="b268e-477">String</span></span>|  
|<span data-ttu-id="b268e-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-479">String</span><span class="sxs-lookup"><span data-stu-id="b268e-479">String</span></span>|  
|<span data-ttu-id="b268e-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b268e-481">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-481">Int16</span></span>|  
|<span data-ttu-id="b268e-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b268e-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b268e-483">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-483">Int16</span></span>|  
|<span data-ttu-id="b268e-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b268e-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b268e-485">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-485">Int16</span></span>|  
|<span data-ttu-id="b268e-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-486">REMARKS</span></span>|<span data-ttu-id="b268e-487">String</span><span class="sxs-lookup"><span data-stu-id="b268e-487">String</span></span>|  
|<span data-ttu-id="b268e-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b268e-489">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b268e-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b268e-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b268e-491">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-491">ColumnName</span></span>|<span data-ttu-id="b268e-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b268e-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b268e-494">String</span><span class="sxs-lookup"><span data-stu-id="b268e-494">String</span></span>|  
|<span data-ttu-id="b268e-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b268e-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b268e-496">String</span><span class="sxs-lookup"><span data-stu-id="b268e-496">String</span></span>|  
|<span data-ttu-id="b268e-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-498">String</span><span class="sxs-lookup"><span data-stu-id="b268e-498">String</span></span>|  
|<span data-ttu-id="b268e-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-499">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-500">String</span><span class="sxs-lookup"><span data-stu-id="b268e-500">String</span></span>|  
|<span data-ttu-id="b268e-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-501">COLUMN_TYPE</span></span>|<span data-ttu-id="b268e-502">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-502">Int16</span></span>|  
|<span data-ttu-id="b268e-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-503">DATA_TYPE</span></span>|<span data-ttu-id="b268e-504">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-504">Int16</span></span>|  
|<span data-ttu-id="b268e-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-505">TYPE_NAME</span></span>|<span data-ttu-id="b268e-506">String</span><span class="sxs-lookup"><span data-stu-id="b268e-506">String</span></span>|  
|<span data-ttu-id="b268e-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="b268e-507">PRECISION</span></span>|<span data-ttu-id="b268e-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-508">Int32</span></span>|  
|<span data-ttu-id="b268e-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b268e-509">LENGTH</span></span>|<span data-ttu-id="b268e-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-510">Int32</span></span>|  
|<span data-ttu-id="b268e-511">SKALI</span><span class="sxs-lookup"><span data-stu-id="b268e-511">SCALE</span></span>|<span data-ttu-id="b268e-512">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-512">Int16</span></span>|  
|<span data-ttu-id="b268e-513">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="b268e-513">RADIX</span></span>|<span data-ttu-id="b268e-514">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-514">Int16</span></span>|  
|<span data-ttu-id="b268e-515">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-515">NULLABLE</span></span>|<span data-ttu-id="b268e-516">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-516">Int16</span></span>|  
|<span data-ttu-id="b268e-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-517">REMARKS</span></span>|<span data-ttu-id="b268e-518">String</span><span class="sxs-lookup"><span data-stu-id="b268e-518">String</span></span>|  
|<span data-ttu-id="b268e-519">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="b268e-519">OVERLOAD</span></span>|<span data-ttu-id="b268e-520">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-520">Int32</span></span>|  
|<span data-ttu-id="b268e-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-522">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b268e-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b268e-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b268e-524">Element columnName</span><span class="sxs-lookup"><span data-stu-id="b268e-524">ColumnName</span></span>|<span data-ttu-id="b268e-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b268e-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b268e-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b268e-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="b268e-527">String</span><span class="sxs-lookup"><span data-stu-id="b268e-527">String</span></span>|  
|<span data-ttu-id="b268e-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b268e-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b268e-529">String</span><span class="sxs-lookup"><span data-stu-id="b268e-529">String</span></span>|  
|<span data-ttu-id="b268e-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="b268e-531">String</span><span class="sxs-lookup"><span data-stu-id="b268e-531">String</span></span>|  
|<span data-ttu-id="b268e-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-532">COLUMN_NAME</span></span>|<span data-ttu-id="b268e-533">String</span><span class="sxs-lookup"><span data-stu-id="b268e-533">String</span></span>|  
|<span data-ttu-id="b268e-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-534">COLUMN_TYPE</span></span>|<span data-ttu-id="b268e-535">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-535">Int16</span></span>|  
|<span data-ttu-id="b268e-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-536">DATA_TYPE</span></span>|<span data-ttu-id="b268e-537">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-537">Int16</span></span>|  
|<span data-ttu-id="b268e-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b268e-538">TYPE_NAME</span></span>|<span data-ttu-id="b268e-539">String</span><span class="sxs-lookup"><span data-stu-id="b268e-539">String</span></span>|  
|<span data-ttu-id="b268e-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b268e-540">COLUMN_SIZE</span></span>|<span data-ttu-id="b268e-541">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-541">Int32</span></span>|  
|<span data-ttu-id="b268e-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="b268e-543">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-543">Int32</span></span>|  
|<span data-ttu-id="b268e-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b268e-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b268e-545">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-545">Int16</span></span>|  
|<span data-ttu-id="b268e-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b268e-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b268e-547">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-547">Int16</span></span>|  
|<span data-ttu-id="b268e-548">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="b268e-548">NULLABLE</span></span>|<span data-ttu-id="b268e-549">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-549">Int16</span></span>|  
|<span data-ttu-id="b268e-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="b268e-550">REMARKS</span></span>|<span data-ttu-id="b268e-551">String</span><span class="sxs-lookup"><span data-stu-id="b268e-551">String</span></span>|  
|<span data-ttu-id="b268e-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b268e-552">COLUMN_DEF</span></span>|<span data-ttu-id="b268e-553">String</span><span class="sxs-lookup"><span data-stu-id="b268e-553">String</span></span>|  
|<span data-ttu-id="b268e-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b268e-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b268e-555">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-555">Int16</span></span>|  
|<span data-ttu-id="b268e-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b268e-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b268e-557">Int16</span><span class="sxs-lookup"><span data-stu-id="b268e-557">Int16</span></span>|  
|<span data-ttu-id="b268e-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b268e-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b268e-559">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-559">Int32</span></span>|  
|<span data-ttu-id="b268e-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b268e-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="b268e-561">Int32</span><span class="sxs-lookup"><span data-stu-id="b268e-561">Int32</span></span>|  
|<span data-ttu-id="b268e-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b268e-562">IS_NULLABLE</span></span>|<span data-ttu-id="b268e-563">String</span><span class="sxs-lookup"><span data-stu-id="b268e-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b268e-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b268e-564">See Also</span></span>  
 [<span data-ttu-id="b268e-565">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b268e-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
