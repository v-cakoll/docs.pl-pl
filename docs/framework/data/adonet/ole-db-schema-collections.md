---
title: "Kolekcje schematów OLE DB"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="34b73-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="34b73-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="34b73-103">W tej sekcji omówiono obsługi kolekcji schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="34b73-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="34b73-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="34b73-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="34b73-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="34b73-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="34b73-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-106">Tables</span></span>  
  
-   <span data-ttu-id="34b73-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-107">Columns</span></span>  
  
-   <span data-ttu-id="34b73-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-108">Procedures</span></span>  
  
-   <span data-ttu-id="34b73-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="34b73-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="34b73-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="34b73-110">Catalog</span></span>  
  
-   <span data-ttu-id="34b73-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="34b73-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-112">Tables</span></span>  
  
|<span data-ttu-id="34b73-113">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-113">ColumnName</span></span>|<span data-ttu-id="34b73-114">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-115">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-116">String</span><span class="sxs-lookup"><span data-stu-id="34b73-116">String</span></span>|  
|<span data-ttu-id="34b73-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-118">String</span><span class="sxs-lookup"><span data-stu-id="34b73-118">String</span></span>|  
|<span data-ttu-id="34b73-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-119">TABLE_NAME</span></span>|<span data-ttu-id="34b73-120">String</span><span class="sxs-lookup"><span data-stu-id="34b73-120">String</span></span>|  
|<span data-ttu-id="34b73-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-121">TABLE_TYPE</span></span>|<span data-ttu-id="34b73-122">String</span><span class="sxs-lookup"><span data-stu-id="34b73-122">String</span></span>|  
|<span data-ttu-id="34b73-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-123">TABLE_GUID</span></span>|<span data-ttu-id="34b73-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-124">Guid</span></span>|  
|<span data-ttu-id="34b73-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-125">DESCRIPTION</span></span>|<span data-ttu-id="34b73-126">String</span><span class="sxs-lookup"><span data-stu-id="34b73-126">String</span></span>|  
|<span data-ttu-id="34b73-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-127">TABLE_PROPID</span></span>|<span data-ttu-id="34b73-128">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-128">Int64</span></span>|  
|<span data-ttu-id="34b73-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-129">DATE_CREATED</span></span>|<span data-ttu-id="34b73-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-130">DateTime</span></span>|  
|<span data-ttu-id="34b73-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-131">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="34b73-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-133">Columns</span></span>  
  
|<span data-ttu-id="34b73-134">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-134">ColumnName</span></span>|<span data-ttu-id="34b73-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-136">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-137">String</span><span class="sxs-lookup"><span data-stu-id="34b73-137">String</span></span>|  
|<span data-ttu-id="34b73-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-139">String</span><span class="sxs-lookup"><span data-stu-id="34b73-139">String</span></span>|  
|<span data-ttu-id="34b73-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-140">TABLE_NAME</span></span>|<span data-ttu-id="34b73-141">String</span><span class="sxs-lookup"><span data-stu-id="34b73-141">String</span></span>|  
|<span data-ttu-id="34b73-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-142">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-143">String</span><span class="sxs-lookup"><span data-stu-id="34b73-143">String</span></span>|  
|<span data-ttu-id="34b73-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-144">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-145">Guid</span></span>|  
|<span data-ttu-id="34b73-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-146">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-147">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-147">Int64</span></span>|  
|<span data-ttu-id="34b73-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-149">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-149">Int64</span></span>|  
|<span data-ttu-id="34b73-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="34b73-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-151">Boolean</span></span>|  
|<span data-ttu-id="34b73-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="34b73-153">String</span><span class="sxs-lookup"><span data-stu-id="34b73-153">String</span></span>|  
|<span data-ttu-id="34b73-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="34b73-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="34b73-155">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-155">Int64</span></span>|  
|<span data-ttu-id="34b73-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-156">IS_NULLABLE</span></span>|<span data-ttu-id="34b73-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-157">Boolean</span></span>|  
|<span data-ttu-id="34b73-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-158">DATA_TYPE</span></span>|<span data-ttu-id="34b73-159">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-159">Int32</span></span>|  
|<span data-ttu-id="34b73-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-160">TYPE_GUID</span></span>|<span data-ttu-id="34b73-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-161">Guid</span></span>|  
|<span data-ttu-id="34b73-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="34b73-163">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-163">Int64</span></span>|  
|<span data-ttu-id="34b73-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="34b73-165">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-165">Int64</span></span>|  
|<span data-ttu-id="34b73-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="34b73-167">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-167">Int32</span></span>|  
|<span data-ttu-id="34b73-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="34b73-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="34b73-169">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-169">Int16</span></span>|  
|<span data-ttu-id="34b73-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="34b73-171">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-171">Int64</span></span>|  
|<span data-ttu-id="34b73-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="34b73-173">String</span><span class="sxs-lookup"><span data-stu-id="34b73-173">String</span></span>|  
|<span data-ttu-id="34b73-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="34b73-175">String</span><span class="sxs-lookup"><span data-stu-id="34b73-175">String</span></span>|  
|<span data-ttu-id="34b73-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="34b73-177">String</span><span class="sxs-lookup"><span data-stu-id="34b73-177">String</span></span>|  
|<span data-ttu-id="34b73-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="34b73-179">String</span><span class="sxs-lookup"><span data-stu-id="34b73-179">String</span></span>|  
|<span data-ttu-id="34b73-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="34b73-181">String</span><span class="sxs-lookup"><span data-stu-id="34b73-181">String</span></span>|  
|<span data-ttu-id="34b73-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-182">COLLATION_NAME</span></span>|<span data-ttu-id="34b73-183">String</span><span class="sxs-lookup"><span data-stu-id="34b73-183">String</span></span>|  
|<span data-ttu-id="34b73-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="34b73-185">String</span><span class="sxs-lookup"><span data-stu-id="34b73-185">String</span></span>|  
|<span data-ttu-id="34b73-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="34b73-187">String</span><span class="sxs-lookup"><span data-stu-id="34b73-187">String</span></span>|  
|<span data-ttu-id="34b73-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-188">DOMAIN_NAME</span></span>|<span data-ttu-id="34b73-189">String</span><span class="sxs-lookup"><span data-stu-id="34b73-189">String</span></span>|  
|<span data-ttu-id="34b73-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-190">DESCRIPTION</span></span>|<span data-ttu-id="34b73-191">String</span><span class="sxs-lookup"><span data-stu-id="34b73-191">String</span></span>|  
|<span data-ttu-id="34b73-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="34b73-192">COLUMN_LCID</span></span>|<span data-ttu-id="34b73-193">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-193">Int32</span></span>|  
|<span data-ttu-id="34b73-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="34b73-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="34b73-195">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-195">Int32</span></span>|  
|<span data-ttu-id="34b73-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="34b73-196">COLUMN_SORTID</span></span>|<span data-ttu-id="34b73-197">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-197">Int32</span></span>|  
|<span data-ttu-id="34b73-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="34b73-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="34b73-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="34b73-199">Byte[]</span></span>|  
|<span data-ttu-id="34b73-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="34b73-200">IS_COMPUTED</span></span>|<span data-ttu-id="34b73-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="34b73-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-202">Procedures</span></span>  
  
|<span data-ttu-id="34b73-203">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-203">ColumnName</span></span>|<span data-ttu-id="34b73-204">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="34b73-206">String</span><span class="sxs-lookup"><span data-stu-id="34b73-206">String</span></span>|  
|<span data-ttu-id="34b73-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="34b73-208">String</span><span class="sxs-lookup"><span data-stu-id="34b73-208">String</span></span>|  
|<span data-ttu-id="34b73-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="34b73-210">String</span><span class="sxs-lookup"><span data-stu-id="34b73-210">String</span></span>|  
|<span data-ttu-id="34b73-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="34b73-212">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-212">Int16</span></span>|  
|<span data-ttu-id="34b73-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="34b73-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="34b73-214">String</span><span class="sxs-lookup"><span data-stu-id="34b73-214">String</span></span>|  
|<span data-ttu-id="34b73-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-215">DESCRIPTION</span></span>|<span data-ttu-id="34b73-216">String</span><span class="sxs-lookup"><span data-stu-id="34b73-216">String</span></span>|  
|<span data-ttu-id="34b73-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-217">DATE_CREATED</span></span>|<span data-ttu-id="34b73-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-218">DateTime</span></span>|  
|<span data-ttu-id="34b73-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-219">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="34b73-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="34b73-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="34b73-222">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-222">ColumnName</span></span>|<span data-ttu-id="34b73-223">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="34b73-225">String</span><span class="sxs-lookup"><span data-stu-id="34b73-225">String</span></span>|  
|<span data-ttu-id="34b73-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="34b73-227">String</span><span class="sxs-lookup"><span data-stu-id="34b73-227">String</span></span>|  
|<span data-ttu-id="34b73-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="34b73-229">String</span><span class="sxs-lookup"><span data-stu-id="34b73-229">String</span></span>|  
|<span data-ttu-id="34b73-230">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="34b73-230">PARAMETER_NAME</span></span>|<span data-ttu-id="34b73-231">String</span><span class="sxs-lookup"><span data-stu-id="34b73-231">String</span></span>|  
|<span data-ttu-id="34b73-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-233">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-233">Int32</span></span>|  
|<span data-ttu-id="34b73-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="34b73-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="34b73-235">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-235">Int32</span></span>|  
|<span data-ttu-id="34b73-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="34b73-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-237">Boolean</span></span>|  
|<span data-ttu-id="34b73-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="34b73-239">String</span><span class="sxs-lookup"><span data-stu-id="34b73-239">String</span></span>|  
|<span data-ttu-id="34b73-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-240">IS_NULLABLE</span></span>|<span data-ttu-id="34b73-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-241">Boolean</span></span>|  
|<span data-ttu-id="34b73-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-242">DATA_TYPE</span></span>|<span data-ttu-id="34b73-243">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-243">Int32</span></span>|  
|<span data-ttu-id="34b73-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="34b73-245">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-245">Int64</span></span>|  
|<span data-ttu-id="34b73-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="34b73-247">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-247">Int64</span></span>|  
|<span data-ttu-id="34b73-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="34b73-249">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-249">Int32</span></span>|  
|<span data-ttu-id="34b73-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="34b73-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="34b73-251">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-251">Int16</span></span>|  
|<span data-ttu-id="34b73-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-252">DESCRIPTION</span></span>|<span data-ttu-id="34b73-253">String</span><span class="sxs-lookup"><span data-stu-id="34b73-253">String</span></span>|  
|<span data-ttu-id="34b73-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-254">TYPE_NAME</span></span>|<span data-ttu-id="34b73-255">String</span><span class="sxs-lookup"><span data-stu-id="34b73-255">String</span></span>|  
|<span data-ttu-id="34b73-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="34b73-257">String</span><span class="sxs-lookup"><span data-stu-id="34b73-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="34b73-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="34b73-258">Catalog</span></span>  
  
|<span data-ttu-id="34b73-259">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-259">ColumnName</span></span>|<span data-ttu-id="34b73-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-261">CATALOG_NAME</span></span>|<span data-ttu-id="34b73-262">String</span><span class="sxs-lookup"><span data-stu-id="34b73-262">String</span></span>|  
|<span data-ttu-id="34b73-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-263">DESCRIPTION</span></span>|<span data-ttu-id="34b73-264">String</span><span class="sxs-lookup"><span data-stu-id="34b73-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="34b73-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-265">Indexes</span></span>  
  
|<span data-ttu-id="34b73-266">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-266">ColumnName</span></span>|<span data-ttu-id="34b73-267">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-268">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-269">String</span><span class="sxs-lookup"><span data-stu-id="34b73-269">String</span></span>|  
|<span data-ttu-id="34b73-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-271">String</span><span class="sxs-lookup"><span data-stu-id="34b73-271">String</span></span>|  
|<span data-ttu-id="34b73-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-272">TABLE_NAME</span></span>|<span data-ttu-id="34b73-273">String</span><span class="sxs-lookup"><span data-stu-id="34b73-273">String</span></span>|  
|<span data-ttu-id="34b73-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-274">INDEX_CATALOG</span></span>|<span data-ttu-id="34b73-275">String</span><span class="sxs-lookup"><span data-stu-id="34b73-275">String</span></span>|  
|<span data-ttu-id="34b73-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="34b73-277">String</span><span class="sxs-lookup"><span data-stu-id="34b73-277">String</span></span>|  
|<span data-ttu-id="34b73-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-278">INDEX_NAME</span></span>|<span data-ttu-id="34b73-279">String</span><span class="sxs-lookup"><span data-stu-id="34b73-279">String</span></span>|  
|<span data-ttu-id="34b73-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="34b73-280">PRIMARY_KEY</span></span>|<span data-ttu-id="34b73-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-281">Boolean</span></span>|  
|<span data-ttu-id="34b73-282">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="34b73-282">UNIQUE</span></span>|<span data-ttu-id="34b73-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-283">Boolean</span></span>|  
|<span data-ttu-id="34b73-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="34b73-284">CLUSTERED</span></span>|<span data-ttu-id="34b73-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-285">Boolean</span></span>|  
|<span data-ttu-id="34b73-286">TYP</span><span class="sxs-lookup"><span data-stu-id="34b73-286">TYPE</span></span>|<span data-ttu-id="34b73-287">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-287">Int32</span></span>|  
|<span data-ttu-id="34b73-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="34b73-288">FILL_FACTOR</span></span>|<span data-ttu-id="34b73-289">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-289">Int32</span></span>|  
|<span data-ttu-id="34b73-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="34b73-290">INITIAL_SIZE</span></span>|<span data-ttu-id="34b73-291">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-291">Int32</span></span>|  
|<span data-ttu-id="34b73-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="34b73-292">NULLS</span></span>|<span data-ttu-id="34b73-293">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-293">Int32</span></span>|  
|<span data-ttu-id="34b73-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="34b73-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="34b73-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-295">Boolean</span></span>|  
|<span data-ttu-id="34b73-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="34b73-296">AUTO_UPDATE</span></span>|<span data-ttu-id="34b73-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-297">Boolean</span></span>|  
|<span data-ttu-id="34b73-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="34b73-298">NULL_COLLATION</span></span>|<span data-ttu-id="34b73-299">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-299">Int32</span></span>|  
|<span data-ttu-id="34b73-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-301">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-301">Int64</span></span>|  
|<span data-ttu-id="34b73-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-302">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-303">String</span><span class="sxs-lookup"><span data-stu-id="34b73-303">String</span></span>|  
|<span data-ttu-id="34b73-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-304">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-305">Guid</span></span>|  
|<span data-ttu-id="34b73-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-306">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-307">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-307">Int64</span></span>|  
|<span data-ttu-id="34b73-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="34b73-308">COLLATION</span></span>|<span data-ttu-id="34b73-309">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-309">Int16</span></span>|  
|<span data-ttu-id="34b73-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="34b73-310">CARDINALITY</span></span>|<span data-ttu-id="34b73-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="34b73-311">Decimal</span></span>|  
|<span data-ttu-id="34b73-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="34b73-312">PAGES</span></span>|<span data-ttu-id="34b73-313">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-313">Int32</span></span>|  
|<span data-ttu-id="34b73-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="34b73-314">FILTER_CONDITION</span></span>|<span data-ttu-id="34b73-315">String</span><span class="sxs-lookup"><span data-stu-id="34b73-315">String</span></span>|  
|<span data-ttu-id="34b73-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="34b73-316">INTEGRATED</span></span>|<span data-ttu-id="34b73-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="34b73-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="34b73-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="34b73-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="34b73-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="34b73-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-320">Tables</span></span>  
  
-   <span data-ttu-id="34b73-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-321">Columns</span></span>  
  
-   <span data-ttu-id="34b73-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-322">Procedures</span></span>  
  
-   <span data-ttu-id="34b73-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="34b73-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="34b73-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="34b73-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="34b73-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="34b73-325">Views</span></span>  
  
-   <span data-ttu-id="34b73-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="34b73-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-327">Tables</span></span>  
  
|<span data-ttu-id="34b73-328">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-328">ColumnName</span></span>|<span data-ttu-id="34b73-329">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-330">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-331">String</span><span class="sxs-lookup"><span data-stu-id="34b73-331">String</span></span>|  
|<span data-ttu-id="34b73-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-333">String</span><span class="sxs-lookup"><span data-stu-id="34b73-333">String</span></span>|  
|<span data-ttu-id="34b73-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-334">TABLE_NAME</span></span>|<span data-ttu-id="34b73-335">String</span><span class="sxs-lookup"><span data-stu-id="34b73-335">String</span></span>|  
|<span data-ttu-id="34b73-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-336">TABLE_TYPE</span></span>|<span data-ttu-id="34b73-337">String</span><span class="sxs-lookup"><span data-stu-id="34b73-337">String</span></span>|  
|<span data-ttu-id="34b73-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-338">TABLE_GUID</span></span>|<span data-ttu-id="34b73-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-339">Guid</span></span>|  
|<span data-ttu-id="34b73-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-340">DESCRIPTION</span></span>|<span data-ttu-id="34b73-341">String</span><span class="sxs-lookup"><span data-stu-id="34b73-341">String</span></span>|  
|<span data-ttu-id="34b73-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-342">TABLE_PROPID</span></span>|<span data-ttu-id="34b73-343">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-343">Int64</span></span>|  
|<span data-ttu-id="34b73-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-344">DATE_CREATED</span></span>|<span data-ttu-id="34b73-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-345">DateTime</span></span>|  
|<span data-ttu-id="34b73-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-346">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="34b73-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-348">Columns</span></span>  
  
|<span data-ttu-id="34b73-349">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-349">ColumnName</span></span>|<span data-ttu-id="34b73-350">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-351">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-352">String</span><span class="sxs-lookup"><span data-stu-id="34b73-352">String</span></span>|  
|<span data-ttu-id="34b73-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-354">String</span><span class="sxs-lookup"><span data-stu-id="34b73-354">String</span></span>|  
|<span data-ttu-id="34b73-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-355">TABLE_NAME</span></span>|<span data-ttu-id="34b73-356">String</span><span class="sxs-lookup"><span data-stu-id="34b73-356">String</span></span>|  
|<span data-ttu-id="34b73-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-357">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-358">String</span><span class="sxs-lookup"><span data-stu-id="34b73-358">String</span></span>|  
|<span data-ttu-id="34b73-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-359">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-360">Guid</span></span>|  
|<span data-ttu-id="34b73-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-361">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-362">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-362">Int64</span></span>|  
|<span data-ttu-id="34b73-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-364">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-364">Int64</span></span>|  
|<span data-ttu-id="34b73-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="34b73-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-366">Boolean</span></span>|  
|<span data-ttu-id="34b73-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="34b73-368">String</span><span class="sxs-lookup"><span data-stu-id="34b73-368">String</span></span>|  
|<span data-ttu-id="34b73-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="34b73-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="34b73-370">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-370">Int64</span></span>|  
|<span data-ttu-id="34b73-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-371">IS_NULLABLE</span></span>|<span data-ttu-id="34b73-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-372">Boolean</span></span>|  
|<span data-ttu-id="34b73-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-373">DATA_TYPE</span></span>|<span data-ttu-id="34b73-374">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-374">Int32</span></span>|  
|<span data-ttu-id="34b73-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-375">TYPE_GUID</span></span>|<span data-ttu-id="34b73-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-376">Guid</span></span>|  
|<span data-ttu-id="34b73-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="34b73-378">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-378">Int64</span></span>|  
|<span data-ttu-id="34b73-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="34b73-380">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-380">Int64</span></span>|  
|<span data-ttu-id="34b73-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="34b73-382">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-382">Int32</span></span>|  
|<span data-ttu-id="34b73-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="34b73-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="34b73-384">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-384">Int16</span></span>|  
|<span data-ttu-id="34b73-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="34b73-386">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-386">Int64</span></span>|  
|<span data-ttu-id="34b73-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="34b73-388">String</span><span class="sxs-lookup"><span data-stu-id="34b73-388">String</span></span>|  
|<span data-ttu-id="34b73-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="34b73-390">String</span><span class="sxs-lookup"><span data-stu-id="34b73-390">String</span></span>|  
|<span data-ttu-id="34b73-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="34b73-392">String</span><span class="sxs-lookup"><span data-stu-id="34b73-392">String</span></span>|  
|<span data-ttu-id="34b73-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="34b73-394">String</span><span class="sxs-lookup"><span data-stu-id="34b73-394">String</span></span>|  
|<span data-ttu-id="34b73-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="34b73-396">String</span><span class="sxs-lookup"><span data-stu-id="34b73-396">String</span></span>|  
|<span data-ttu-id="34b73-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-397">COLLATION_NAME</span></span>|<span data-ttu-id="34b73-398">String</span><span class="sxs-lookup"><span data-stu-id="34b73-398">String</span></span>|  
|<span data-ttu-id="34b73-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="34b73-400">String</span><span class="sxs-lookup"><span data-stu-id="34b73-400">String</span></span>|  
|<span data-ttu-id="34b73-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="34b73-402">String</span><span class="sxs-lookup"><span data-stu-id="34b73-402">String</span></span>|  
|<span data-ttu-id="34b73-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-403">DOMAIN_NAME</span></span>|<span data-ttu-id="34b73-404">String</span><span class="sxs-lookup"><span data-stu-id="34b73-404">String</span></span>|  
|<span data-ttu-id="34b73-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-405">DESCRIPTION</span></span>|<span data-ttu-id="34b73-406">String</span><span class="sxs-lookup"><span data-stu-id="34b73-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="34b73-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-407">Procedures</span></span>  
  
|<span data-ttu-id="34b73-408">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-408">ColumnName</span></span>|<span data-ttu-id="34b73-409">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="34b73-411">String</span><span class="sxs-lookup"><span data-stu-id="34b73-411">String</span></span>|  
|<span data-ttu-id="34b73-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="34b73-413">String</span><span class="sxs-lookup"><span data-stu-id="34b73-413">String</span></span>|  
|<span data-ttu-id="34b73-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="34b73-415">String</span><span class="sxs-lookup"><span data-stu-id="34b73-415">String</span></span>|  
|<span data-ttu-id="34b73-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="34b73-417">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-417">Int16</span></span>|  
|<span data-ttu-id="34b73-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="34b73-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="34b73-419">String</span><span class="sxs-lookup"><span data-stu-id="34b73-419">String</span></span>|  
|<span data-ttu-id="34b73-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-420">DESCRIPTION</span></span>|<span data-ttu-id="34b73-421">String</span><span class="sxs-lookup"><span data-stu-id="34b73-421">String</span></span>|  
|<span data-ttu-id="34b73-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-422">DATE_CREATED</span></span>|<span data-ttu-id="34b73-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-423">DateTime</span></span>|  
|<span data-ttu-id="34b73-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-424">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="34b73-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="34b73-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="34b73-427">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-427">ColumnName</span></span>|<span data-ttu-id="34b73-428">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="34b73-430">String</span><span class="sxs-lookup"><span data-stu-id="34b73-430">String</span></span>|  
|<span data-ttu-id="34b73-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="34b73-432">String</span><span class="sxs-lookup"><span data-stu-id="34b73-432">String</span></span>|  
|<span data-ttu-id="34b73-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="34b73-434">String</span><span class="sxs-lookup"><span data-stu-id="34b73-434">String</span></span>|  
|<span data-ttu-id="34b73-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-435">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-436">String</span><span class="sxs-lookup"><span data-stu-id="34b73-436">String</span></span>|  
|<span data-ttu-id="34b73-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-437">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-438">Guid</span></span>|  
|<span data-ttu-id="34b73-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-439">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-440">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-440">Int64</span></span>|  
|<span data-ttu-id="34b73-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="34b73-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="34b73-442">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-442">Int64</span></span>|  
|<span data-ttu-id="34b73-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-444">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-444">Int64</span></span>|  
|<span data-ttu-id="34b73-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-445">IS_NULLABLE</span></span>|<span data-ttu-id="34b73-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-446">Boolean</span></span>|  
|<span data-ttu-id="34b73-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-447">DATA_TYPE</span></span>|<span data-ttu-id="34b73-448">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-448">Int32</span></span>|  
|<span data-ttu-id="34b73-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-449">TYPE_GUID</span></span>|<span data-ttu-id="34b73-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-450">Guid</span></span>|  
|<span data-ttu-id="34b73-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="34b73-452">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-452">Int64</span></span>|  
|<span data-ttu-id="34b73-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="34b73-454">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-454">Int64</span></span>|  
|<span data-ttu-id="34b73-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="34b73-456">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-456">Int32</span></span>|  
|<span data-ttu-id="34b73-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="34b73-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="34b73-458">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-458">Int16</span></span>|  
|<span data-ttu-id="34b73-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-459">DESCRIPTION</span></span>|<span data-ttu-id="34b73-460">String</span><span class="sxs-lookup"><span data-stu-id="34b73-460">String</span></span>|  
|<span data-ttu-id="34b73-461">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="34b73-461">OVERLOAD</span></span>|<span data-ttu-id="34b73-462">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="34b73-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="34b73-463">Views</span></span>  
  
|<span data-ttu-id="34b73-464">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-464">ColumnName</span></span>|<span data-ttu-id="34b73-465">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-466">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-467">String</span><span class="sxs-lookup"><span data-stu-id="34b73-467">String</span></span>|  
|<span data-ttu-id="34b73-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-469">String</span><span class="sxs-lookup"><span data-stu-id="34b73-469">String</span></span>|  
|<span data-ttu-id="34b73-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-470">TABLE_NAME</span></span>|<span data-ttu-id="34b73-471">String</span><span class="sxs-lookup"><span data-stu-id="34b73-471">String</span></span>|  
|<span data-ttu-id="34b73-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="34b73-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="34b73-473">String</span><span class="sxs-lookup"><span data-stu-id="34b73-473">String</span></span>|  
|<span data-ttu-id="34b73-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="34b73-474">CHECK_OPTION</span></span>|<span data-ttu-id="34b73-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-475">Boolean</span></span>|  
|<span data-ttu-id="34b73-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-476">IS_UPDATABLE</span></span>|<span data-ttu-id="34b73-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-477">Boolean</span></span>|  
|<span data-ttu-id="34b73-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-478">DESCRIPTION</span></span>|<span data-ttu-id="34b73-479">String</span><span class="sxs-lookup"><span data-stu-id="34b73-479">String</span></span>|  
|<span data-ttu-id="34b73-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-480">DATE_CREATED</span></span>|<span data-ttu-id="34b73-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-481">DateTime</span></span>|  
|<span data-ttu-id="34b73-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-482">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="34b73-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-484">Indexes</span></span>  
  
|<span data-ttu-id="34b73-485">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-485">ColumnName</span></span>|<span data-ttu-id="34b73-486">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-487">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-488">String</span><span class="sxs-lookup"><span data-stu-id="34b73-488">String</span></span>|  
|<span data-ttu-id="34b73-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-490">String</span><span class="sxs-lookup"><span data-stu-id="34b73-490">String</span></span>|  
|<span data-ttu-id="34b73-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-491">TABLE_NAME</span></span>|<span data-ttu-id="34b73-492">String</span><span class="sxs-lookup"><span data-stu-id="34b73-492">String</span></span>|  
|<span data-ttu-id="34b73-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-493">INDEX_CATALOG</span></span>|<span data-ttu-id="34b73-494">String</span><span class="sxs-lookup"><span data-stu-id="34b73-494">String</span></span>|  
|<span data-ttu-id="34b73-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="34b73-496">String</span><span class="sxs-lookup"><span data-stu-id="34b73-496">String</span></span>|  
|<span data-ttu-id="34b73-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-497">INDEX_NAME</span></span>|<span data-ttu-id="34b73-498">String</span><span class="sxs-lookup"><span data-stu-id="34b73-498">String</span></span>|  
|<span data-ttu-id="34b73-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="34b73-499">PRIMARY_KEY</span></span>|<span data-ttu-id="34b73-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-500">Boolean</span></span>|  
|<span data-ttu-id="34b73-501">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="34b73-501">UNIQUE</span></span>|<span data-ttu-id="34b73-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-502">Boolean</span></span>|  
|<span data-ttu-id="34b73-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="34b73-503">CLUSTERED</span></span>|<span data-ttu-id="34b73-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-504">Boolean</span></span>|  
|<span data-ttu-id="34b73-505">TYP</span><span class="sxs-lookup"><span data-stu-id="34b73-505">TYPE</span></span>|<span data-ttu-id="34b73-506">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-506">Int32</span></span>|  
|<span data-ttu-id="34b73-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="34b73-507">FILL_FACTOR</span></span>|<span data-ttu-id="34b73-508">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-508">Int32</span></span>|  
|<span data-ttu-id="34b73-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="34b73-509">INITIAL_SIZE</span></span>|<span data-ttu-id="34b73-510">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-510">Int32</span></span>|  
|<span data-ttu-id="34b73-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="34b73-511">NULLS</span></span>|<span data-ttu-id="34b73-512">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-512">Int32</span></span>|  
|<span data-ttu-id="34b73-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="34b73-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="34b73-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-514">Boolean</span></span>|  
|<span data-ttu-id="34b73-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="34b73-515">AUTO_UPDATE</span></span>|<span data-ttu-id="34b73-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-516">Boolean</span></span>|  
|<span data-ttu-id="34b73-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="34b73-517">NULL_COLLATION</span></span>|<span data-ttu-id="34b73-518">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-518">Int32</span></span>|  
|<span data-ttu-id="34b73-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-520">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-520">Int64</span></span>|  
|<span data-ttu-id="34b73-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-521">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-522">String</span><span class="sxs-lookup"><span data-stu-id="34b73-522">String</span></span>|  
|<span data-ttu-id="34b73-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-523">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-524">Guid</span></span>|  
|<span data-ttu-id="34b73-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-525">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-526">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-526">Int64</span></span>|  
|<span data-ttu-id="34b73-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="34b73-527">COLLATION</span></span>|<span data-ttu-id="34b73-528">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-528">Int16</span></span>|  
|<span data-ttu-id="34b73-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="34b73-529">CARDINALITY</span></span>|<span data-ttu-id="34b73-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="34b73-530">Decimal</span></span>|  
|<span data-ttu-id="34b73-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="34b73-531">PAGES</span></span>|<span data-ttu-id="34b73-532">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-532">Int32</span></span>|  
|<span data-ttu-id="34b73-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="34b73-533">FILTER_CONDITION</span></span>|<span data-ttu-id="34b73-534">String</span><span class="sxs-lookup"><span data-stu-id="34b73-534">String</span></span>|  
|<span data-ttu-id="34b73-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="34b73-535">INTEGRATED</span></span>|<span data-ttu-id="34b73-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="34b73-537">Dostawca programu Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="34b73-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="34b73-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="34b73-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="34b73-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-539">Tables</span></span>  
  
-   <span data-ttu-id="34b73-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-540">Columns</span></span>  
  
-   <span data-ttu-id="34b73-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-541">Procedures</span></span>  
  
-   <span data-ttu-id="34b73-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="34b73-542">Views</span></span>  
  
-   <span data-ttu-id="34b73-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="34b73-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="34b73-544">Tables</span></span>  
  
|<span data-ttu-id="34b73-545">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-545">ColumnName</span></span>|<span data-ttu-id="34b73-546">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-547">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-548">String</span><span class="sxs-lookup"><span data-stu-id="34b73-548">String</span></span>|  
|<span data-ttu-id="34b73-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-550">String</span><span class="sxs-lookup"><span data-stu-id="34b73-550">String</span></span>|  
|<span data-ttu-id="34b73-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-551">TABLE_NAME</span></span>|<span data-ttu-id="34b73-552">String</span><span class="sxs-lookup"><span data-stu-id="34b73-552">String</span></span>|  
|<span data-ttu-id="34b73-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-553">TABLE_TYPE</span></span>|<span data-ttu-id="34b73-554">String</span><span class="sxs-lookup"><span data-stu-id="34b73-554">String</span></span>|  
|<span data-ttu-id="34b73-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-555">TABLE_GUID</span></span>|<span data-ttu-id="34b73-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-556">Guid</span></span>|  
|<span data-ttu-id="34b73-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-557">DESCRIPTION</span></span>|<span data-ttu-id="34b73-558">String</span><span class="sxs-lookup"><span data-stu-id="34b73-558">String</span></span>|  
|<span data-ttu-id="34b73-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-559">TABLE_PROPID</span></span>|<span data-ttu-id="34b73-560">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-560">Int64</span></span>|  
|<span data-ttu-id="34b73-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-561">DATE_CREATED</span></span>|<span data-ttu-id="34b73-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-562">DateTime</span></span>|  
|<span data-ttu-id="34b73-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-563">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="34b73-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="34b73-565">Columns</span></span>  
  
|<span data-ttu-id="34b73-566">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-566">ColumnName</span></span>|<span data-ttu-id="34b73-567">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-568">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-569">String</span><span class="sxs-lookup"><span data-stu-id="34b73-569">String</span></span>|  
|<span data-ttu-id="34b73-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-571">String</span><span class="sxs-lookup"><span data-stu-id="34b73-571">String</span></span>|  
|<span data-ttu-id="34b73-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-572">TABLE_NAME</span></span>|<span data-ttu-id="34b73-573">String</span><span class="sxs-lookup"><span data-stu-id="34b73-573">String</span></span>|  
|<span data-ttu-id="34b73-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-574">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-575">String</span><span class="sxs-lookup"><span data-stu-id="34b73-575">String</span></span>|  
|<span data-ttu-id="34b73-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-576">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-577">Guid</span></span>|  
|<span data-ttu-id="34b73-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-578">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-579">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-579">Int64</span></span>|  
|<span data-ttu-id="34b73-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-581">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-581">Int64</span></span>|  
|<span data-ttu-id="34b73-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="34b73-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-583">Boolean</span></span>|  
|<span data-ttu-id="34b73-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="34b73-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="34b73-585">String</span><span class="sxs-lookup"><span data-stu-id="34b73-585">String</span></span>|  
|<span data-ttu-id="34b73-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="34b73-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="34b73-587">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-587">Int64</span></span>|  
|<span data-ttu-id="34b73-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-588">IS_NULLABLE</span></span>|<span data-ttu-id="34b73-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-589">Boolean</span></span>|  
|<span data-ttu-id="34b73-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-590">DATA_TYPE</span></span>|<span data-ttu-id="34b73-591">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-591">Int32</span></span>|  
|<span data-ttu-id="34b73-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-592">TYPE_GUID</span></span>|<span data-ttu-id="34b73-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-593">Guid</span></span>|  
|<span data-ttu-id="34b73-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="34b73-595">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-595">Int64</span></span>|  
|<span data-ttu-id="34b73-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="34b73-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="34b73-597">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-597">Int64</span></span>|  
|<span data-ttu-id="34b73-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="34b73-599">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-599">Int32</span></span>|  
|<span data-ttu-id="34b73-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="34b73-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="34b73-601">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-601">Int16</span></span>|  
|<span data-ttu-id="34b73-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="34b73-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="34b73-603">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-603">Int64</span></span>|  
|<span data-ttu-id="34b73-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="34b73-605">String</span><span class="sxs-lookup"><span data-stu-id="34b73-605">String</span></span>|  
|<span data-ttu-id="34b73-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="34b73-607">String</span><span class="sxs-lookup"><span data-stu-id="34b73-607">String</span></span>|  
|<span data-ttu-id="34b73-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="34b73-609">String</span><span class="sxs-lookup"><span data-stu-id="34b73-609">String</span></span>|  
|<span data-ttu-id="34b73-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="34b73-611">String</span><span class="sxs-lookup"><span data-stu-id="34b73-611">String</span></span>|  
|<span data-ttu-id="34b73-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="34b73-613">String</span><span class="sxs-lookup"><span data-stu-id="34b73-613">String</span></span>|  
|<span data-ttu-id="34b73-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-614">COLLATION_NAME</span></span>|<span data-ttu-id="34b73-615">String</span><span class="sxs-lookup"><span data-stu-id="34b73-615">String</span></span>|  
|<span data-ttu-id="34b73-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="34b73-617">String</span><span class="sxs-lookup"><span data-stu-id="34b73-617">String</span></span>|  
|<span data-ttu-id="34b73-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="34b73-619">String</span><span class="sxs-lookup"><span data-stu-id="34b73-619">String</span></span>|  
|<span data-ttu-id="34b73-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-620">DOMAIN_NAME</span></span>|<span data-ttu-id="34b73-621">String</span><span class="sxs-lookup"><span data-stu-id="34b73-621">String</span></span>|  
|<span data-ttu-id="34b73-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-622">DESCRIPTION</span></span>|<span data-ttu-id="34b73-623">String</span><span class="sxs-lookup"><span data-stu-id="34b73-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="34b73-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="34b73-624">Procedures</span></span>  
  
|<span data-ttu-id="34b73-625">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-625">ColumnName</span></span>|<span data-ttu-id="34b73-626">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="34b73-628">String</span><span class="sxs-lookup"><span data-stu-id="34b73-628">String</span></span>|  
|<span data-ttu-id="34b73-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="34b73-630">String</span><span class="sxs-lookup"><span data-stu-id="34b73-630">String</span></span>|  
|<span data-ttu-id="34b73-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="34b73-632">String</span><span class="sxs-lookup"><span data-stu-id="34b73-632">String</span></span>|  
|<span data-ttu-id="34b73-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="34b73-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="34b73-634">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-634">Int16</span></span>|  
|<span data-ttu-id="34b73-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="34b73-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="34b73-636">String</span><span class="sxs-lookup"><span data-stu-id="34b73-636">String</span></span>|  
|<span data-ttu-id="34b73-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-637">DESCRIPTION</span></span>|<span data-ttu-id="34b73-638">String</span><span class="sxs-lookup"><span data-stu-id="34b73-638">String</span></span>|  
|<span data-ttu-id="34b73-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-639">DATE_CREATED</span></span>|<span data-ttu-id="34b73-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-640">DateTime</span></span>|  
|<span data-ttu-id="34b73-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-641">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="34b73-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="34b73-643">Views</span></span>  
  
|<span data-ttu-id="34b73-644">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-644">ColumnName</span></span>|<span data-ttu-id="34b73-645">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-646">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-647">String</span><span class="sxs-lookup"><span data-stu-id="34b73-647">String</span></span>|  
|<span data-ttu-id="34b73-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-649">String</span><span class="sxs-lookup"><span data-stu-id="34b73-649">String</span></span>|  
|<span data-ttu-id="34b73-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-650">TABLE_NAME</span></span>|<span data-ttu-id="34b73-651">String</span><span class="sxs-lookup"><span data-stu-id="34b73-651">String</span></span>|  
|<span data-ttu-id="34b73-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="34b73-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="34b73-653">String</span><span class="sxs-lookup"><span data-stu-id="34b73-653">String</span></span>|  
|<span data-ttu-id="34b73-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="34b73-654">CHECK_OPTION</span></span>|<span data-ttu-id="34b73-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-655">Boolean</span></span>|  
|<span data-ttu-id="34b73-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="34b73-656">IS_UPDATABLE</span></span>|<span data-ttu-id="34b73-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-657">Boolean</span></span>|  
|<span data-ttu-id="34b73-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="34b73-658">DESCRIPTION</span></span>|<span data-ttu-id="34b73-659">String</span><span class="sxs-lookup"><span data-stu-id="34b73-659">String</span></span>|  
|<span data-ttu-id="34b73-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="34b73-660">DATE_CREATED</span></span>|<span data-ttu-id="34b73-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-661">DateTime</span></span>|  
|<span data-ttu-id="34b73-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="34b73-662">DATE_MODIFIED</span></span>|<span data-ttu-id="34b73-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="34b73-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="34b73-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="34b73-664">Indexes</span></span>  
  
|<span data-ttu-id="34b73-665">Element columnName</span><span class="sxs-lookup"><span data-stu-id="34b73-665">ColumnName</span></span>|<span data-ttu-id="34b73-666">Typ danych</span><span class="sxs-lookup"><span data-stu-id="34b73-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="34b73-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-667">TABLE_CATALOG</span></span>|<span data-ttu-id="34b73-668">String</span><span class="sxs-lookup"><span data-stu-id="34b73-668">String</span></span>|  
|<span data-ttu-id="34b73-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="34b73-670">String</span><span class="sxs-lookup"><span data-stu-id="34b73-670">String</span></span>|  
|<span data-ttu-id="34b73-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-671">TABLE_NAME</span></span>|<span data-ttu-id="34b73-672">String</span><span class="sxs-lookup"><span data-stu-id="34b73-672">String</span></span>|  
|<span data-ttu-id="34b73-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="34b73-673">INDEX_CATALOG</span></span>|<span data-ttu-id="34b73-674">String</span><span class="sxs-lookup"><span data-stu-id="34b73-674">String</span></span>|  
|<span data-ttu-id="34b73-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="34b73-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="34b73-676">String</span><span class="sxs-lookup"><span data-stu-id="34b73-676">String</span></span>|  
|<span data-ttu-id="34b73-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-677">INDEX_NAME</span></span>|<span data-ttu-id="34b73-678">String</span><span class="sxs-lookup"><span data-stu-id="34b73-678">String</span></span>|  
|<span data-ttu-id="34b73-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="34b73-679">PRIMARY_KEY</span></span>|<span data-ttu-id="34b73-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-680">Boolean</span></span>|  
|<span data-ttu-id="34b73-681">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="34b73-681">UNIQUE</span></span>|<span data-ttu-id="34b73-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-682">Boolean</span></span>|  
|<span data-ttu-id="34b73-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="34b73-683">CLUSTERED</span></span>|<span data-ttu-id="34b73-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-684">Boolean</span></span>|  
|<span data-ttu-id="34b73-685">TYP</span><span class="sxs-lookup"><span data-stu-id="34b73-685">TYPE</span></span>|<span data-ttu-id="34b73-686">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-686">Int32</span></span>|  
|<span data-ttu-id="34b73-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="34b73-687">FILL_FACTOR</span></span>|<span data-ttu-id="34b73-688">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-688">Int32</span></span>|  
|<span data-ttu-id="34b73-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="34b73-689">INITIAL_SIZE</span></span>|<span data-ttu-id="34b73-690">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-690">Int32</span></span>|  
|<span data-ttu-id="34b73-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="34b73-691">NULLS</span></span>|<span data-ttu-id="34b73-692">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-692">Int32</span></span>|  
|<span data-ttu-id="34b73-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="34b73-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="34b73-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-694">Boolean</span></span>|  
|<span data-ttu-id="34b73-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="34b73-695">AUTO_UPDATE</span></span>|<span data-ttu-id="34b73-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-696">Boolean</span></span>|  
|<span data-ttu-id="34b73-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="34b73-697">NULL_COLLATION</span></span>|<span data-ttu-id="34b73-698">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-698">Int32</span></span>|  
|<span data-ttu-id="34b73-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="34b73-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="34b73-700">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-700">Int64</span></span>|  
|<span data-ttu-id="34b73-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="34b73-701">COLUMN_NAME</span></span>|<span data-ttu-id="34b73-702">String</span><span class="sxs-lookup"><span data-stu-id="34b73-702">String</span></span>|  
|<span data-ttu-id="34b73-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-703">COLUMN_GUID</span></span>|<span data-ttu-id="34b73-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="34b73-704">Guid</span></span>|  
|<span data-ttu-id="34b73-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="34b73-705">COLUMN_PROPID</span></span>|<span data-ttu-id="34b73-706">Int64</span><span class="sxs-lookup"><span data-stu-id="34b73-706">Int64</span></span>|  
|<span data-ttu-id="34b73-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="34b73-707">COLLATION</span></span>|<span data-ttu-id="34b73-708">Int16</span><span class="sxs-lookup"><span data-stu-id="34b73-708">Int16</span></span>|  
|<span data-ttu-id="34b73-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="34b73-709">CARDINALITY</span></span>|<span data-ttu-id="34b73-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="34b73-710">Decimal</span></span>|  
|<span data-ttu-id="34b73-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="34b73-711">PAGES</span></span>|<span data-ttu-id="34b73-712">Int32</span><span class="sxs-lookup"><span data-stu-id="34b73-712">Int32</span></span>|  
|<span data-ttu-id="34b73-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="34b73-713">FILTER_CONDITION</span></span>|<span data-ttu-id="34b73-714">String</span><span class="sxs-lookup"><span data-stu-id="34b73-714">String</span></span>|  
|<span data-ttu-id="34b73-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="34b73-715">INTEGRATED</span></span>|<span data-ttu-id="34b73-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="34b73-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34b73-717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34b73-717">See Also</span></span>  
 [<span data-ttu-id="34b73-718">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="34b73-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
