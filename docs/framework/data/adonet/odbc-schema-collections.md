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
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="2e1c3-102">Kolekcje schematów ODBC</span><span class="sxs-lookup"><span data-stu-id="2e1c3-102">ODBC Schema Collections</span></span>
<span data-ttu-id="2e1c3-103">W tej sekcji omówiono obsługi kolekcji schematu dla sterowników ODBC dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="2e1c3-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="2e1c3-104">Sterownik ODBC programu Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="2e1c3-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="2e1c3-105">Sterownik ODBC programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2e1c3-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2e1c3-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="2e1c3-106">Tables</span></span>  
  
-   <span data-ttu-id="2e1c3-107">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2e1c3-107">Indexes</span></span>  
  
-   <span data-ttu-id="2e1c3-108">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-108">Columns</span></span>  
  
-   <span data-ttu-id="2e1c3-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-109">Procedures</span></span>  
  
-   <span data-ttu-id="2e1c3-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2e1c3-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2e1c3-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2e1c3-112">Widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2e1c3-113">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-113">Tables and Views</span></span>  
  
|<span data-ttu-id="2e1c3-114">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-114">ColumnName</span></span>|<span data-ttu-id="2e1c3-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-116">TABLE_CAT</span></span>|<span data-ttu-id="2e1c3-117">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-117">String</span></span>|  
|<span data-ttu-id="2e1c3-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-118">TABLE_SCHEM</span></span>|<span data-ttu-id="2e1c3-119">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-119">String</span></span>|  
|<span data-ttu-id="2e1c3-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-120">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-121">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-121">String</span></span>|  
|<span data-ttu-id="2e1c3-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-122">TABLE_TYPE</span></span>|<span data-ttu-id="2e1c3-123">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-123">String</span></span>|  
|<span data-ttu-id="2e1c3-124">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-124">REMARKS</span></span>|<span data-ttu-id="2e1c3-125">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2e1c3-126">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2e1c3-126">Indexes</span></span>  
  
|<span data-ttu-id="2e1c3-127">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-127">ColumnName</span></span>|<span data-ttu-id="2e1c3-128">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-129">TABLE_CAT</span></span>|<span data-ttu-id="2e1c3-130">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-130">String</span></span>|  
|<span data-ttu-id="2e1c3-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-131">TABLE_SCHEM</span></span>|<span data-ttu-id="2e1c3-132">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-132">String</span></span>|  
|<span data-ttu-id="2e1c3-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-133">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-134">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-134">String</span></span>|  
|<span data-ttu-id="2e1c3-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-135">NON_UNIQUE</span></span>|<span data-ttu-id="2e1c3-136">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-136">Int16</span></span>|  
|<span data-ttu-id="2e1c3-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-138">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-138">String</span></span>|  
|<span data-ttu-id="2e1c3-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-139">INDEX_NAME</span></span>|<span data-ttu-id="2e1c3-140">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-140">String</span></span>|  
|<span data-ttu-id="2e1c3-141">TYP</span><span class="sxs-lookup"><span data-stu-id="2e1c3-141">TYPE</span></span>|<span data-ttu-id="2e1c3-142">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-142">Int16</span></span>|  
|<span data-ttu-id="2e1c3-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-144">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-144">Int16</span></span>|  
|<span data-ttu-id="2e1c3-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-145">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-146">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-146">String</span></span>|  
|<span data-ttu-id="2e1c3-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="2e1c3-147">ASC_OR_DESC</span></span>|<span data-ttu-id="2e1c3-148">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-148">String</span></span>|  
|<span data-ttu-id="2e1c3-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="2e1c3-149">CARDINATLITY</span></span>|<span data-ttu-id="2e1c3-150">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-150">Int32</span></span>|  
|<span data-ttu-id="2e1c3-151">STRONY</span><span class="sxs-lookup"><span data-stu-id="2e1c3-151">PAGES</span></span>|<span data-ttu-id="2e1c3-152">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-152">Int32</span></span>|  
|<span data-ttu-id="2e1c3-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-153">FILTER_CONDITION</span></span>|<span data-ttu-id="2e1c3-154">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-154">String</span></span>|  
|<span data-ttu-id="2e1c3-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2e1c3-156">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-156">String</span></span>|  
|<span data-ttu-id="2e1c3-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-158">Byte</span><span class="sxs-lookup"><span data-stu-id="2e1c3-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2e1c3-159">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-159">Columns</span></span>  
  
|<span data-ttu-id="2e1c3-160">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-160">ColumnName</span></span>|<span data-ttu-id="2e1c3-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-162">TABLE_CAT</span></span>|<span data-ttu-id="2e1c3-163">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-163">String</span></span>|  
|<span data-ttu-id="2e1c3-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-164">TABLE_SCHEM</span></span>|<span data-ttu-id="2e1c3-165">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-165">String</span></span>|  
|<span data-ttu-id="2e1c3-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-166">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-167">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-167">String</span></span>|  
|<span data-ttu-id="2e1c3-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-168">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-169">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-169">String</span></span>|  
|<span data-ttu-id="2e1c3-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-170">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-171">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-171">Int16</span></span>|  
|<span data-ttu-id="2e1c3-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-172">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-173">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-173">String</span></span>|  
|<span data-ttu-id="2e1c3-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-174">COLUMN_SIZE</span></span>|<span data-ttu-id="2e1c3-175">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-175">Int32</span></span>|  
|<span data-ttu-id="2e1c3-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="2e1c3-177">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-177">Int32</span></span>|  
|<span data-ttu-id="2e1c3-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2e1c3-179">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-179">Int16</span></span>|  
|<span data-ttu-id="2e1c3-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2e1c3-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2e1c3-181">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-181">Int16</span></span>|  
|<span data-ttu-id="2e1c3-182">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-182">NULLABLE</span></span>|<span data-ttu-id="2e1c3-183">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-183">Int16</span></span>|  
|<span data-ttu-id="2e1c3-184">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-184">REMARKS</span></span>|<span data-ttu-id="2e1c3-185">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-185">String</span></span>|  
|<span data-ttu-id="2e1c3-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2e1c3-186">COLUMN_DEF</span></span>|<span data-ttu-id="2e1c3-187">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-187">String</span></span>|  
|<span data-ttu-id="2e1c3-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-189">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-189">Int16</span></span>|  
|<span data-ttu-id="2e1c3-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2e1c3-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2e1c3-191">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-191">Int16</span></span>|  
|<span data-ttu-id="2e1c3-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2e1c3-193">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-193">Int32</span></span>|  
|<span data-ttu-id="2e1c3-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-195">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-195">Int32</span></span>|  
|<span data-ttu-id="2e1c3-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-196">IS_NULLABLE</span></span>|<span data-ttu-id="2e1c3-197">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-197">String</span></span>|  
|<span data-ttu-id="2e1c3-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2e1c3-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2e1c3-199">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-199">String</span></span>|  
|<span data-ttu-id="2e1c3-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2e1c3-201">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-201">String</span></span>|  
|<span data-ttu-id="2e1c3-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-203">Byte</span><span class="sxs-lookup"><span data-stu-id="2e1c3-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2e1c3-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-204">Procedures</span></span>  
  
|<span data-ttu-id="2e1c3-205">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-205">ColumnName</span></span>|<span data-ttu-id="2e1c3-206">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="2e1c3-208">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-208">String</span></span>|  
|<span data-ttu-id="2e1c3-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2e1c3-210">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-210">String</span></span>|  
|<span data-ttu-id="2e1c3-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-212">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-212">String</span></span>|  
|<span data-ttu-id="2e1c3-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-214">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-214">Int32</span></span>|  
|<span data-ttu-id="2e1c3-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-216">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-216">Int32</span></span>|  
|<span data-ttu-id="2e1c3-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2e1c3-218">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-218">Int32</span></span>|  
|<span data-ttu-id="2e1c3-219">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-219">REMARKS</span></span>|<span data-ttu-id="2e1c3-220">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-220">String</span></span>|  
|<span data-ttu-id="2e1c3-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2e1c3-222">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2e1c3-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2e1c3-224">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-224">ColumnName</span></span>|<span data-ttu-id="2e1c3-225">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="2e1c3-227">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-227">String</span></span>|  
|<span data-ttu-id="2e1c3-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2e1c3-229">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-229">String</span></span>|  
|<span data-ttu-id="2e1c3-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-231">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-231">String</span></span>|  
|<span data-ttu-id="2e1c3-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-232">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-233">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-233">String</span></span>|  
|<span data-ttu-id="2e1c3-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-234">COLUMN_TYPE</span></span>|<span data-ttu-id="2e1c3-235">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-235">Int16</span></span>|  
|<span data-ttu-id="2e1c3-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-236">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-237">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-237">Int16</span></span>|  
|<span data-ttu-id="2e1c3-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-238">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-239">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-239">String</span></span>|  
|<span data-ttu-id="2e1c3-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-240">COLUMN_SIZE</span></span>|<span data-ttu-id="2e1c3-241">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-241">Int32</span></span>|  
|<span data-ttu-id="2e1c3-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="2e1c3-243">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-243">Int32</span></span>|  
|<span data-ttu-id="2e1c3-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2e1c3-245">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-245">Int16</span></span>|  
|<span data-ttu-id="2e1c3-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2e1c3-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2e1c3-247">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-247">Int16</span></span>|  
|<span data-ttu-id="2e1c3-248">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-248">NULLABLE</span></span>|<span data-ttu-id="2e1c3-249">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-249">Int16</span></span>|  
|<span data-ttu-id="2e1c3-250">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-250">REMARKS</span></span>|<span data-ttu-id="2e1c3-251">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-251">String</span></span>|  
|<span data-ttu-id="2e1c3-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2e1c3-252">COLUMN_DEF</span></span>|<span data-ttu-id="2e1c3-253">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-253">String</span></span>|  
|<span data-ttu-id="2e1c3-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-255">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-255">Int16</span></span>|  
|<span data-ttu-id="2e1c3-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2e1c3-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2e1c3-257">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-257">Int16</span></span>|  
|<span data-ttu-id="2e1c3-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2e1c3-259">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-259">Int32</span></span>|  
|<span data-ttu-id="2e1c3-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-261">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-261">Int32</span></span>|  
|<span data-ttu-id="2e1c3-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-262">IS_NULLABLE</span></span>|<span data-ttu-id="2e1c3-263">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-263">String</span></span>|  
|<span data-ttu-id="2e1c3-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2e1c3-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2e1c3-265">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-265">String</span></span>|  
|<span data-ttu-id="2e1c3-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2e1c3-267">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-267">String</span></span>|  
|<span data-ttu-id="2e1c3-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-269">Byte</span><span class="sxs-lookup"><span data-stu-id="2e1c3-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2e1c3-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2e1c3-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2e1c3-271">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-271">ColumnName</span></span>|<span data-ttu-id="2e1c3-272">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="2e1c3-274">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-274">String</span></span>|  
|<span data-ttu-id="2e1c3-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2e1c3-276">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-276">String</span></span>|  
|<span data-ttu-id="2e1c3-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-278">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-278">String</span></span>|  
|<span data-ttu-id="2e1c3-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-279">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-280">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-280">String</span></span>|  
|<span data-ttu-id="2e1c3-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-281">COLUMN_TYPE</span></span>|<span data-ttu-id="2e1c3-282">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-282">Int16</span></span>|  
|<span data-ttu-id="2e1c3-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-283">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-284">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-284">Int16</span></span>|  
|<span data-ttu-id="2e1c3-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-285">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-286">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-286">String</span></span>|  
|<span data-ttu-id="2e1c3-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-287">COLUMN_SIZE</span></span>|<span data-ttu-id="2e1c3-288">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-288">Int32</span></span>|  
|<span data-ttu-id="2e1c3-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="2e1c3-290">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-290">Int32</span></span>|  
|<span data-ttu-id="2e1c3-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2e1c3-292">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-292">Int16</span></span>|  
|<span data-ttu-id="2e1c3-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2e1c3-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2e1c3-294">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-294">Int16</span></span>|  
|<span data-ttu-id="2e1c3-295">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-295">NULLABLE</span></span>|<span data-ttu-id="2e1c3-296">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-296">Int16</span></span>|  
|<span data-ttu-id="2e1c3-297">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-297">REMARKS</span></span>|<span data-ttu-id="2e1c3-298">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-298">String</span></span>|  
|<span data-ttu-id="2e1c3-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2e1c3-299">COLUMN_DEF</span></span>|<span data-ttu-id="2e1c3-300">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-300">String</span></span>|  
|<span data-ttu-id="2e1c3-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-302">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-302">Int16</span></span>|  
|<span data-ttu-id="2e1c3-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2e1c3-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2e1c3-304">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-304">Int16</span></span>|  
|<span data-ttu-id="2e1c3-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2e1c3-306">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-306">Int32</span></span>|  
|<span data-ttu-id="2e1c3-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-308">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-308">Int32</span></span>|  
|<span data-ttu-id="2e1c3-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-309">IS_NULLABLE</span></span>|<span data-ttu-id="2e1c3-310">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-310">String</span></span>|  
|<span data-ttu-id="2e1c3-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2e1c3-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="2e1c3-312">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-312">String</span></span>|  
|<span data-ttu-id="2e1c3-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="2e1c3-314">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-314">String</span></span>|  
|<span data-ttu-id="2e1c3-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-316">Byte</span><span class="sxs-lookup"><span data-stu-id="2e1c3-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="2e1c3-317">Sterownik ODBC rozwiązań Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="2e1c3-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="2e1c3-318">Sterownik ODBC programu Oracle do programu Microsoft SQL Server obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2e1c3-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2e1c3-319">Tabele</span><span class="sxs-lookup"><span data-stu-id="2e1c3-319">Tables</span></span>  
  
-   <span data-ttu-id="2e1c3-320">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-320">Columns</span></span>  
  
-   <span data-ttu-id="2e1c3-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-321">Procedures</span></span>  
  
-   <span data-ttu-id="2e1c3-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2e1c3-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2e1c3-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2e1c3-324">Widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-324">Views</span></span>  
  
-   <span data-ttu-id="2e1c3-325">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2e1c3-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2e1c3-326">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-326">Tables and Views</span></span>  
  
|<span data-ttu-id="2e1c3-327">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-327">ColumnName</span></span>|<span data-ttu-id="2e1c3-328">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-330">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-330">String</span></span>|  
|<span data-ttu-id="2e1c3-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-331">TABLE_OWNER</span></span>|<span data-ttu-id="2e1c3-332">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-332">String</span></span>|  
|<span data-ttu-id="2e1c3-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-333">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-334">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-334">String</span></span>|  
|<span data-ttu-id="2e1c3-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-335">TABLE_TYPE</span></span>|<span data-ttu-id="2e1c3-336">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-336">String</span></span>|  
|<span data-ttu-id="2e1c3-337">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-337">REMARKS</span></span>|<span data-ttu-id="2e1c3-338">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2e1c3-339">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-339">Columns</span></span>  
  
|<span data-ttu-id="2e1c3-340">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-340">ColumnName</span></span>|<span data-ttu-id="2e1c3-341">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-343">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-343">String</span></span>|  
|<span data-ttu-id="2e1c3-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-344">TABLE_OWNER</span></span>|<span data-ttu-id="2e1c3-345">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-345">String</span></span>|  
|<span data-ttu-id="2e1c3-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-346">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-347">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-347">String</span></span>|  
|<span data-ttu-id="2e1c3-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-348">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-349">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-349">String</span></span>|  
|<span data-ttu-id="2e1c3-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-350">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-351">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-351">Int16</span></span>|  
|<span data-ttu-id="2e1c3-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-352">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-353">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-353">String</span></span>|  
|<span data-ttu-id="2e1c3-354">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-354">PRECISION</span></span>|<span data-ttu-id="2e1c3-355">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-355">Int32</span></span>|  
|<span data-ttu-id="2e1c3-356">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-356">LENGTH</span></span>|<span data-ttu-id="2e1c3-357">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-357">Int32</span></span>|  
|<span data-ttu-id="2e1c3-358">SKALI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-358">SCALE</span></span>|<span data-ttu-id="2e1c3-359">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-359">Int16</span></span>|  
|<span data-ttu-id="2e1c3-360">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-360">RADIX</span></span>|<span data-ttu-id="2e1c3-361">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-361">Int16</span></span>|  
|<span data-ttu-id="2e1c3-362">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-362">NULLABLE</span></span>|<span data-ttu-id="2e1c3-363">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-363">Int16</span></span>|  
|<span data-ttu-id="2e1c3-364">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-364">REMARKS</span></span>|<span data-ttu-id="2e1c3-365">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-365">String</span></span>|  
|<span data-ttu-id="2e1c3-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-367">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2e1c3-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-368">Procedures</span></span>  
  
|<span data-ttu-id="2e1c3-369">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-369">ColumnName</span></span>|<span data-ttu-id="2e1c3-370">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-372">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-372">String</span></span>|  
|<span data-ttu-id="2e1c3-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2e1c3-374">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-374">String</span></span>|  
|<span data-ttu-id="2e1c3-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-376">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-376">String</span></span>|  
|<span data-ttu-id="2e1c3-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-378">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-378">Int16</span></span>|  
|<span data-ttu-id="2e1c3-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-380">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-380">Int16</span></span>|  
|<span data-ttu-id="2e1c3-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2e1c3-382">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-382">Int16</span></span>|  
|<span data-ttu-id="2e1c3-383">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-383">REMARKS</span></span>|<span data-ttu-id="2e1c3-384">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-384">String</span></span>|  
|<span data-ttu-id="2e1c3-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2e1c3-386">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2e1c3-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2e1c3-388">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-388">ColumnName</span></span>|<span data-ttu-id="2e1c3-389">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-391">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-391">String</span></span>|  
|<span data-ttu-id="2e1c3-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2e1c3-393">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-393">String</span></span>|  
|<span data-ttu-id="2e1c3-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-395">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-395">String</span></span>|  
|<span data-ttu-id="2e1c3-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-396">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-397">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-397">String</span></span>|  
|<span data-ttu-id="2e1c3-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-398">COLUMN_TYPE</span></span>|<span data-ttu-id="2e1c3-399">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-399">Int16</span></span>|  
|<span data-ttu-id="2e1c3-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-400">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-401">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-401">Int16</span></span>|  
|<span data-ttu-id="2e1c3-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-402">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-403">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-403">String</span></span>|  
|<span data-ttu-id="2e1c3-404">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-404">PRECISION</span></span>|<span data-ttu-id="2e1c3-405">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-405">Int32</span></span>|  
|<span data-ttu-id="2e1c3-406">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-406">LENGTH</span></span>|<span data-ttu-id="2e1c3-407">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-407">Int32</span></span>|  
|<span data-ttu-id="2e1c3-408">SKALI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-408">SCALE</span></span>|<span data-ttu-id="2e1c3-409">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-409">Int16</span></span>|  
|<span data-ttu-id="2e1c3-410">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-410">RADIX</span></span>|<span data-ttu-id="2e1c3-411">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-411">Int16</span></span>|  
|<span data-ttu-id="2e1c3-412">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-412">NULLABLE</span></span>|<span data-ttu-id="2e1c3-413">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-413">Int16</span></span>|  
|<span data-ttu-id="2e1c3-414">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-414">REMARKS</span></span>|<span data-ttu-id="2e1c3-415">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-415">String</span></span>|  
|<span data-ttu-id="2e1c3-416">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-416">OVERLOAD</span></span>|<span data-ttu-id="2e1c3-417">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-417">Int32</span></span>|  
|<span data-ttu-id="2e1c3-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-419">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="2e1c3-420">Sterownik ODBC dla programu Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="2e1c3-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="2e1c3-421">Sterownik ODBC firmy Microsoft Jet obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2e1c3-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2e1c3-422">Tabele</span><span class="sxs-lookup"><span data-stu-id="2e1c3-422">Tables</span></span>  
  
-   <span data-ttu-id="2e1c3-423">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2e1c3-423">Indexes</span></span>  
  
-   <span data-ttu-id="2e1c3-424">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-424">Columns</span></span>  
  
-   <span data-ttu-id="2e1c3-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-425">Procedures</span></span>  
  
-   <span data-ttu-id="2e1c3-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2e1c3-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2e1c3-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2e1c3-428">Widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="2e1c3-429">Tabele i widoki</span><span class="sxs-lookup"><span data-stu-id="2e1c3-429">Tables and Views</span></span>  
  
|<span data-ttu-id="2e1c3-430">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-430">ColumnName</span></span>|<span data-ttu-id="2e1c3-431">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-433">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-433">String</span></span>|  
|<span data-ttu-id="2e1c3-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-434">TABLE_OWNER</span></span>|<span data-ttu-id="2e1c3-435">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-435">String</span></span>|  
|<span data-ttu-id="2e1c3-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-436">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-437">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-437">String</span></span>|  
|<span data-ttu-id="2e1c3-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-438">TABLE_TYPE</span></span>|<span data-ttu-id="2e1c3-439">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-439">String</span></span>|  
|<span data-ttu-id="2e1c3-440">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-440">REMARKS</span></span>|<span data-ttu-id="2e1c3-441">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2e1c3-442">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2e1c3-442">Columns</span></span>  
  
|<span data-ttu-id="2e1c3-443">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-443">ColumnName</span></span>|<span data-ttu-id="2e1c3-444">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-446">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-446">String</span></span>|  
|<span data-ttu-id="2e1c3-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-447">TABLE_OWNER</span></span>|<span data-ttu-id="2e1c3-448">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-448">String</span></span>|  
|<span data-ttu-id="2e1c3-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-449">TABLE_NAME</span></span>|<span data-ttu-id="2e1c3-450">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-450">String</span></span>|  
|<span data-ttu-id="2e1c3-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-451">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-452">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-452">String</span></span>|  
|<span data-ttu-id="2e1c3-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-453">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-454">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-454">Int16</span></span>|  
|<span data-ttu-id="2e1c3-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-455">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-456">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-456">String</span></span>|  
|<span data-ttu-id="2e1c3-457">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-457">PRECISION</span></span>|<span data-ttu-id="2e1c3-458">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-458">Int32</span></span>|  
|<span data-ttu-id="2e1c3-459">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-459">LENGTH</span></span>|<span data-ttu-id="2e1c3-460">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-460">Int32</span></span>|  
|<span data-ttu-id="2e1c3-461">SKALI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-461">SCALE</span></span>|<span data-ttu-id="2e1c3-462">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-462">Int16</span></span>|  
|<span data-ttu-id="2e1c3-463">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-463">RADIX</span></span>|<span data-ttu-id="2e1c3-464">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-464">Int16</span></span>|  
|<span data-ttu-id="2e1c3-465">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-465">NULLABLE</span></span>|<span data-ttu-id="2e1c3-466">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-466">Int16</span></span>|  
|<span data-ttu-id="2e1c3-467">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-467">REMARKS</span></span>|<span data-ttu-id="2e1c3-468">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-468">String</span></span>|  
|<span data-ttu-id="2e1c3-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-470">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2e1c3-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="2e1c3-471">Procedures</span></span>  
  
|<span data-ttu-id="2e1c3-472">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-472">ColumnName</span></span>|<span data-ttu-id="2e1c3-473">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-475">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-475">String</span></span>|  
|<span data-ttu-id="2e1c3-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2e1c3-477">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-477">String</span></span>|  
|<span data-ttu-id="2e1c3-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-479">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-479">String</span></span>|  
|<span data-ttu-id="2e1c3-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-481">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-481">Int16</span></span>|  
|<span data-ttu-id="2e1c3-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="2e1c3-483">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-483">Int16</span></span>|  
|<span data-ttu-id="2e1c3-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="2e1c3-485">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-485">Int16</span></span>|  
|<span data-ttu-id="2e1c3-486">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-486">REMARKS</span></span>|<span data-ttu-id="2e1c3-487">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-487">String</span></span>|  
|<span data-ttu-id="2e1c3-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2e1c3-489">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2e1c3-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2e1c3-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2e1c3-491">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-491">ColumnName</span></span>|<span data-ttu-id="2e1c3-492">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="2e1c3-494">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-494">String</span></span>|  
|<span data-ttu-id="2e1c3-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e1c3-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="2e1c3-496">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-496">String</span></span>|  
|<span data-ttu-id="2e1c3-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-498">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-498">String</span></span>|  
|<span data-ttu-id="2e1c3-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-499">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-500">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-500">String</span></span>|  
|<span data-ttu-id="2e1c3-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-501">COLUMN_TYPE</span></span>|<span data-ttu-id="2e1c3-502">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-502">Int16</span></span>|  
|<span data-ttu-id="2e1c3-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-503">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-504">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-504">Int16</span></span>|  
|<span data-ttu-id="2e1c3-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-505">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-506">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-506">String</span></span>|  
|<span data-ttu-id="2e1c3-507">DOKŁADNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-507">PRECISION</span></span>|<span data-ttu-id="2e1c3-508">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-508">Int32</span></span>|  
|<span data-ttu-id="2e1c3-509">DŁUGOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2e1c3-509">LENGTH</span></span>|<span data-ttu-id="2e1c3-510">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-510">Int32</span></span>|  
|<span data-ttu-id="2e1c3-511">SKALI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-511">SCALE</span></span>|<span data-ttu-id="2e1c3-512">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-512">Int16</span></span>|  
|<span data-ttu-id="2e1c3-513">PODSTAWA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-513">RADIX</span></span>|<span data-ttu-id="2e1c3-514">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-514">Int16</span></span>|  
|<span data-ttu-id="2e1c3-515">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-515">NULLABLE</span></span>|<span data-ttu-id="2e1c3-516">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-516">Int16</span></span>|  
|<span data-ttu-id="2e1c3-517">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-517">REMARKS</span></span>|<span data-ttu-id="2e1c3-518">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-518">String</span></span>|  
|<span data-ttu-id="2e1c3-519">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="2e1c3-519">OVERLOAD</span></span>|<span data-ttu-id="2e1c3-520">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-520">Int32</span></span>|  
|<span data-ttu-id="2e1c3-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-522">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2e1c3-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2e1c3-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2e1c3-524">Element columnName</span><span class="sxs-lookup"><span data-stu-id="2e1c3-524">ColumnName</span></span>|<span data-ttu-id="2e1c3-525">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2e1c3-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2e1c3-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="2e1c3-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="2e1c3-527">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-527">String</span></span>|  
|<span data-ttu-id="2e1c3-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="2e1c3-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="2e1c3-529">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-529">String</span></span>|  
|<span data-ttu-id="2e1c3-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="2e1c3-531">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-531">String</span></span>|  
|<span data-ttu-id="2e1c3-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-532">COLUMN_NAME</span></span>|<span data-ttu-id="2e1c3-533">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-533">String</span></span>|  
|<span data-ttu-id="2e1c3-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-534">COLUMN_TYPE</span></span>|<span data-ttu-id="2e1c3-535">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-535">Int16</span></span>|  
|<span data-ttu-id="2e1c3-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-536">DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-537">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-537">Int16</span></span>|  
|<span data-ttu-id="2e1c3-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2e1c3-538">TYPE_NAME</span></span>|<span data-ttu-id="2e1c3-539">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-539">String</span></span>|  
|<span data-ttu-id="2e1c3-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-540">COLUMN_SIZE</span></span>|<span data-ttu-id="2e1c3-541">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-541">Int32</span></span>|  
|<span data-ttu-id="2e1c3-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="2e1c3-543">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-543">Int32</span></span>|  
|<span data-ttu-id="2e1c3-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="2e1c3-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="2e1c3-545">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-545">Int16</span></span>|  
|<span data-ttu-id="2e1c3-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="2e1c3-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="2e1c3-547">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-547">Int16</span></span>|  
|<span data-ttu-id="2e1c3-548">DOPUSZCZAJĄCE WARTOŚCI ZEROWE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-548">NULLABLE</span></span>|<span data-ttu-id="2e1c3-549">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-549">Int16</span></span>|  
|<span data-ttu-id="2e1c3-550">UWAGI</span><span class="sxs-lookup"><span data-stu-id="2e1c3-550">REMARKS</span></span>|<span data-ttu-id="2e1c3-551">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-551">String</span></span>|  
|<span data-ttu-id="2e1c3-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="2e1c3-552">COLUMN_DEF</span></span>|<span data-ttu-id="2e1c3-553">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-553">String</span></span>|  
|<span data-ttu-id="2e1c3-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="2e1c3-555">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-555">Int16</span></span>|  
|<span data-ttu-id="2e1c3-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="2e1c3-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="2e1c3-557">Int16</span><span class="sxs-lookup"><span data-stu-id="2e1c3-557">Int16</span></span>|  
|<span data-ttu-id="2e1c3-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2e1c3-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="2e1c3-559">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-559">Int32</span></span>|  
|<span data-ttu-id="2e1c3-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2e1c3-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="2e1c3-561">Int32</span><span class="sxs-lookup"><span data-stu-id="2e1c3-561">Int32</span></span>|  
|<span data-ttu-id="2e1c3-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2e1c3-562">IS_NULLABLE</span></span>|<span data-ttu-id="2e1c3-563">String</span><span class="sxs-lookup"><span data-stu-id="2e1c3-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e1c3-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e1c3-564">See Also</span></span>  
 [<span data-ttu-id="2e1c3-565">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="2e1c3-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
