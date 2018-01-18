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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="ef3c8-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="ef3c8-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="ef3c8-103">W tej sekcji omówiono obsługi kolekcji schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="ef3c8-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="ef3c8-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="ef3c8-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="ef3c8-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="ef3c8-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ef3c8-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-106">Tables</span></span>  
  
-   <span data-ttu-id="ef3c8-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-107">Columns</span></span>  
  
-   <span data-ttu-id="ef3c8-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-108">Procedures</span></span>  
  
-   <span data-ttu-id="ef3c8-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ef3c8-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ef3c8-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="ef3c8-110">Catalog</span></span>  
  
-   <span data-ttu-id="ef3c8-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="ef3c8-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-112">Tables</span></span>  
  
|<span data-ttu-id="ef3c8-113">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-113">ColumnName</span></span>|<span data-ttu-id="ef3c8-114">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-115">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-116">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-116">String</span></span>|  
|<span data-ttu-id="ef3c8-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-118">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-118">String</span></span>|  
|<span data-ttu-id="ef3c8-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-119">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-120">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-120">String</span></span>|  
|<span data-ttu-id="ef3c8-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-121">TABLE_TYPE</span></span>|<span data-ttu-id="ef3c8-122">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-122">String</span></span>|  
|<span data-ttu-id="ef3c8-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-123">TABLE_GUID</span></span>|<span data-ttu-id="ef3c8-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-124">Guid</span></span>|  
|<span data-ttu-id="ef3c8-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-125">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-126">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-126">String</span></span>|  
|<span data-ttu-id="ef3c8-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-127">TABLE_PROPID</span></span>|<span data-ttu-id="ef3c8-128">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-128">Int64</span></span>|  
|<span data-ttu-id="ef3c8-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-129">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-130">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-131">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ef3c8-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-133">Columns</span></span>  
  
|<span data-ttu-id="ef3c8-134">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-134">ColumnName</span></span>|<span data-ttu-id="ef3c8-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-136">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-137">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-137">String</span></span>|  
|<span data-ttu-id="ef3c8-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-139">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-139">String</span></span>|  
|<span data-ttu-id="ef3c8-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-140">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-141">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-141">String</span></span>|  
|<span data-ttu-id="ef3c8-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-142">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-143">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-143">String</span></span>|  
|<span data-ttu-id="ef3c8-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-144">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-145">Guid</span></span>|  
|<span data-ttu-id="ef3c8-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-146">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-147">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-147">Int64</span></span>|  
|<span data-ttu-id="ef3c8-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-149">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-149">Int64</span></span>|  
|<span data-ttu-id="ef3c8-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="ef3c8-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-151">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="ef3c8-153">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-153">String</span></span>|  
|<span data-ttu-id="ef3c8-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="ef3c8-155">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-155">Int64</span></span>|  
|<span data-ttu-id="ef3c8-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-156">IS_NULLABLE</span></span>|<span data-ttu-id="ef3c8-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-157">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-158">DATA_TYPE</span></span>|<span data-ttu-id="ef3c8-159">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-159">Int32</span></span>|  
|<span data-ttu-id="ef3c8-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-160">TYPE_GUID</span></span>|<span data-ttu-id="ef3c8-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-161">Guid</span></span>|  
|<span data-ttu-id="ef3c8-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="ef3c8-163">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-163">Int64</span></span>|  
|<span data-ttu-id="ef3c8-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="ef3c8-165">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-165">Int64</span></span>|  
|<span data-ttu-id="ef3c8-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="ef3c8-167">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-167">Int32</span></span>|  
|<span data-ttu-id="ef3c8-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="ef3c8-169">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-169">Int16</span></span>|  
|<span data-ttu-id="ef3c8-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="ef3c8-171">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-171">Int64</span></span>|  
|<span data-ttu-id="ef3c8-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="ef3c8-173">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-173">String</span></span>|  
|<span data-ttu-id="ef3c8-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="ef3c8-175">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-175">String</span></span>|  
|<span data-ttu-id="ef3c8-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="ef3c8-177">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-177">String</span></span>|  
|<span data-ttu-id="ef3c8-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="ef3c8-179">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-179">String</span></span>|  
|<span data-ttu-id="ef3c8-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="ef3c8-181">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-181">String</span></span>|  
|<span data-ttu-id="ef3c8-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-182">COLLATION_NAME</span></span>|<span data-ttu-id="ef3c8-183">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-183">String</span></span>|  
|<span data-ttu-id="ef3c8-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="ef3c8-185">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-185">String</span></span>|  
|<span data-ttu-id="ef3c8-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="ef3c8-187">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-187">String</span></span>|  
|<span data-ttu-id="ef3c8-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-188">DOMAIN_NAME</span></span>|<span data-ttu-id="ef3c8-189">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-189">String</span></span>|  
|<span data-ttu-id="ef3c8-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-190">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-191">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-191">String</span></span>|  
|<span data-ttu-id="ef3c8-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-192">COLUMN_LCID</span></span>|<span data-ttu-id="ef3c8-193">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-193">Int32</span></span>|  
|<span data-ttu-id="ef3c8-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="ef3c8-195">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-195">Int32</span></span>|  
|<span data-ttu-id="ef3c8-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-196">COLUMN_SORTID</span></span>|<span data-ttu-id="ef3c8-197">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-197">Int32</span></span>|  
|<span data-ttu-id="ef3c8-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="ef3c8-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="ef3c8-199">Byte[]</span></span>|  
|<span data-ttu-id="ef3c8-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-200">IS_COMPUTED</span></span>|<span data-ttu-id="ef3c8-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ef3c8-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-202">Procedures</span></span>  
  
|<span data-ttu-id="ef3c8-203">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-203">ColumnName</span></span>|<span data-ttu-id="ef3c8-204">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="ef3c8-206">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-206">String</span></span>|  
|<span data-ttu-id="ef3c8-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-208">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-208">String</span></span>|  
|<span data-ttu-id="ef3c8-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="ef3c8-210">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-210">String</span></span>|  
|<span data-ttu-id="ef3c8-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ef3c8-212">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-212">Int16</span></span>|  
|<span data-ttu-id="ef3c8-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="ef3c8-214">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-214">String</span></span>|  
|<span data-ttu-id="ef3c8-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-215">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-216">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-216">String</span></span>|  
|<span data-ttu-id="ef3c8-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-217">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-218">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-219">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="ef3c8-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ef3c8-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="ef3c8-222">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-222">ColumnName</span></span>|<span data-ttu-id="ef3c8-223">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="ef3c8-225">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-225">String</span></span>|  
|<span data-ttu-id="ef3c8-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-227">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-227">String</span></span>|  
|<span data-ttu-id="ef3c8-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="ef3c8-229">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-229">String</span></span>|  
|<span data-ttu-id="ef3c8-230">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-230">PARAMETER_NAME</span></span>|<span data-ttu-id="ef3c8-231">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-231">String</span></span>|  
|<span data-ttu-id="ef3c8-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-233">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-233">Int32</span></span>|  
|<span data-ttu-id="ef3c8-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="ef3c8-235">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-235">Int32</span></span>|  
|<span data-ttu-id="ef3c8-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="ef3c8-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-237">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="ef3c8-239">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-239">String</span></span>|  
|<span data-ttu-id="ef3c8-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-240">IS_NULLABLE</span></span>|<span data-ttu-id="ef3c8-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-241">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-242">DATA_TYPE</span></span>|<span data-ttu-id="ef3c8-243">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-243">Int32</span></span>|  
|<span data-ttu-id="ef3c8-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="ef3c8-245">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-245">Int64</span></span>|  
|<span data-ttu-id="ef3c8-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="ef3c8-247">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-247">Int64</span></span>|  
|<span data-ttu-id="ef3c8-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="ef3c8-249">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-249">Int32</span></span>|  
|<span data-ttu-id="ef3c8-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="ef3c8-251">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-251">Int16</span></span>|  
|<span data-ttu-id="ef3c8-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-252">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-253">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-253">String</span></span>|  
|<span data-ttu-id="ef3c8-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-254">TYPE_NAME</span></span>|<span data-ttu-id="ef3c8-255">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-255">String</span></span>|  
|<span data-ttu-id="ef3c8-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="ef3c8-257">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="ef3c8-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="ef3c8-258">Catalog</span></span>  
  
|<span data-ttu-id="ef3c8-259">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-259">ColumnName</span></span>|<span data-ttu-id="ef3c8-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-261">CATALOG_NAME</span></span>|<span data-ttu-id="ef3c8-262">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-262">String</span></span>|  
|<span data-ttu-id="ef3c8-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-263">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-264">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="ef3c8-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-265">Indexes</span></span>  
  
|<span data-ttu-id="ef3c8-266">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-266">ColumnName</span></span>|<span data-ttu-id="ef3c8-267">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-268">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-269">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-269">String</span></span>|  
|<span data-ttu-id="ef3c8-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-271">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-271">String</span></span>|  
|<span data-ttu-id="ef3c8-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-272">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-273">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-273">String</span></span>|  
|<span data-ttu-id="ef3c8-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-274">INDEX_CATALOG</span></span>|<span data-ttu-id="ef3c8-275">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-275">String</span></span>|  
|<span data-ttu-id="ef3c8-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="ef3c8-277">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-277">String</span></span>|  
|<span data-ttu-id="ef3c8-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-278">INDEX_NAME</span></span>|<span data-ttu-id="ef3c8-279">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-279">String</span></span>|  
|<span data-ttu-id="ef3c8-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-280">PRIMARY_KEY</span></span>|<span data-ttu-id="ef3c8-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-281">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-282">UNIQUE</span></span>|<span data-ttu-id="ef3c8-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-283">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-284">CLUSTERED</span></span>|<span data-ttu-id="ef3c8-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-285">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-286">TYP</span><span class="sxs-lookup"><span data-stu-id="ef3c8-286">TYPE</span></span>|<span data-ttu-id="ef3c8-287">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-287">Int32</span></span>|  
|<span data-ttu-id="ef3c8-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="ef3c8-288">FILL_FACTOR</span></span>|<span data-ttu-id="ef3c8-289">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-289">Int32</span></span>|  
|<span data-ttu-id="ef3c8-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-290">INITIAL_SIZE</span></span>|<span data-ttu-id="ef3c8-291">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-291">Int32</span></span>|  
|<span data-ttu-id="ef3c8-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="ef3c8-292">NULLS</span></span>|<span data-ttu-id="ef3c8-293">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-293">Int32</span></span>|  
|<span data-ttu-id="ef3c8-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="ef3c8-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-295">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-296">AUTO_UPDATE</span></span>|<span data-ttu-id="ef3c8-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-297">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-298">NULL_COLLATION</span></span>|<span data-ttu-id="ef3c8-299">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-299">Int32</span></span>|  
|<span data-ttu-id="ef3c8-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-301">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-301">Int64</span></span>|  
|<span data-ttu-id="ef3c8-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-302">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-303">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-303">String</span></span>|  
|<span data-ttu-id="ef3c8-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-304">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-305">Guid</span></span>|  
|<span data-ttu-id="ef3c8-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-306">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-307">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-307">Int64</span></span>|  
|<span data-ttu-id="ef3c8-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-308">COLLATION</span></span>|<span data-ttu-id="ef3c8-309">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-309">Int16</span></span>|  
|<span data-ttu-id="ef3c8-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="ef3c8-310">CARDINALITY</span></span>|<span data-ttu-id="ef3c8-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="ef3c8-311">Decimal</span></span>|  
|<span data-ttu-id="ef3c8-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-312">PAGES</span></span>|<span data-ttu-id="ef3c8-313">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-313">Int32</span></span>|  
|<span data-ttu-id="ef3c8-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-314">FILTER_CONDITION</span></span>|<span data-ttu-id="ef3c8-315">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-315">String</span></span>|  
|<span data-ttu-id="ef3c8-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-316">INTEGRATED</span></span>|<span data-ttu-id="ef3c8-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="ef3c8-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="ef3c8-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="ef3c8-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="ef3c8-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ef3c8-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-320">Tables</span></span>  
  
-   <span data-ttu-id="ef3c8-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-321">Columns</span></span>  
  
-   <span data-ttu-id="ef3c8-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-322">Procedures</span></span>  
  
-   <span data-ttu-id="ef3c8-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ef3c8-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="ef3c8-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="ef3c8-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="ef3c8-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="ef3c8-325">Views</span></span>  
  
-   <span data-ttu-id="ef3c8-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="ef3c8-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-327">Tables</span></span>  
  
|<span data-ttu-id="ef3c8-328">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-328">ColumnName</span></span>|<span data-ttu-id="ef3c8-329">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-330">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-331">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-331">String</span></span>|  
|<span data-ttu-id="ef3c8-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-333">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-333">String</span></span>|  
|<span data-ttu-id="ef3c8-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-334">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-335">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-335">String</span></span>|  
|<span data-ttu-id="ef3c8-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-336">TABLE_TYPE</span></span>|<span data-ttu-id="ef3c8-337">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-337">String</span></span>|  
|<span data-ttu-id="ef3c8-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-338">TABLE_GUID</span></span>|<span data-ttu-id="ef3c8-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-339">Guid</span></span>|  
|<span data-ttu-id="ef3c8-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-340">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-341">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-341">String</span></span>|  
|<span data-ttu-id="ef3c8-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-342">TABLE_PROPID</span></span>|<span data-ttu-id="ef3c8-343">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-343">Int64</span></span>|  
|<span data-ttu-id="ef3c8-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-344">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-345">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-346">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ef3c8-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-348">Columns</span></span>  
  
|<span data-ttu-id="ef3c8-349">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-349">ColumnName</span></span>|<span data-ttu-id="ef3c8-350">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-351">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-352">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-352">String</span></span>|  
|<span data-ttu-id="ef3c8-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-354">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-354">String</span></span>|  
|<span data-ttu-id="ef3c8-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-355">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-356">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-356">String</span></span>|  
|<span data-ttu-id="ef3c8-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-357">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-358">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-358">String</span></span>|  
|<span data-ttu-id="ef3c8-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-359">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-360">Guid</span></span>|  
|<span data-ttu-id="ef3c8-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-361">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-362">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-362">Int64</span></span>|  
|<span data-ttu-id="ef3c8-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-364">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-364">Int64</span></span>|  
|<span data-ttu-id="ef3c8-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="ef3c8-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-366">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="ef3c8-368">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-368">String</span></span>|  
|<span data-ttu-id="ef3c8-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="ef3c8-370">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-370">Int64</span></span>|  
|<span data-ttu-id="ef3c8-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-371">IS_NULLABLE</span></span>|<span data-ttu-id="ef3c8-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-372">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-373">DATA_TYPE</span></span>|<span data-ttu-id="ef3c8-374">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-374">Int32</span></span>|  
|<span data-ttu-id="ef3c8-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-375">TYPE_GUID</span></span>|<span data-ttu-id="ef3c8-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-376">Guid</span></span>|  
|<span data-ttu-id="ef3c8-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="ef3c8-378">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-378">Int64</span></span>|  
|<span data-ttu-id="ef3c8-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="ef3c8-380">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-380">Int64</span></span>|  
|<span data-ttu-id="ef3c8-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="ef3c8-382">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-382">Int32</span></span>|  
|<span data-ttu-id="ef3c8-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="ef3c8-384">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-384">Int16</span></span>|  
|<span data-ttu-id="ef3c8-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="ef3c8-386">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-386">Int64</span></span>|  
|<span data-ttu-id="ef3c8-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="ef3c8-388">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-388">String</span></span>|  
|<span data-ttu-id="ef3c8-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="ef3c8-390">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-390">String</span></span>|  
|<span data-ttu-id="ef3c8-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="ef3c8-392">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-392">String</span></span>|  
|<span data-ttu-id="ef3c8-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="ef3c8-394">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-394">String</span></span>|  
|<span data-ttu-id="ef3c8-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="ef3c8-396">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-396">String</span></span>|  
|<span data-ttu-id="ef3c8-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-397">COLLATION_NAME</span></span>|<span data-ttu-id="ef3c8-398">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-398">String</span></span>|  
|<span data-ttu-id="ef3c8-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="ef3c8-400">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-400">String</span></span>|  
|<span data-ttu-id="ef3c8-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="ef3c8-402">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-402">String</span></span>|  
|<span data-ttu-id="ef3c8-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-403">DOMAIN_NAME</span></span>|<span data-ttu-id="ef3c8-404">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-404">String</span></span>|  
|<span data-ttu-id="ef3c8-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-405">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-406">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ef3c8-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-407">Procedures</span></span>  
  
|<span data-ttu-id="ef3c8-408">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-408">ColumnName</span></span>|<span data-ttu-id="ef3c8-409">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="ef3c8-411">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-411">String</span></span>|  
|<span data-ttu-id="ef3c8-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-413">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-413">String</span></span>|  
|<span data-ttu-id="ef3c8-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="ef3c8-415">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-415">String</span></span>|  
|<span data-ttu-id="ef3c8-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ef3c8-417">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-417">Int16</span></span>|  
|<span data-ttu-id="ef3c8-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="ef3c8-419">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-419">String</span></span>|  
|<span data-ttu-id="ef3c8-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-420">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-421">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-421">String</span></span>|  
|<span data-ttu-id="ef3c8-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-422">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-423">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-424">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="ef3c8-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="ef3c8-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="ef3c8-427">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-427">ColumnName</span></span>|<span data-ttu-id="ef3c8-428">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="ef3c8-430">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-430">String</span></span>|  
|<span data-ttu-id="ef3c8-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-432">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-432">String</span></span>|  
|<span data-ttu-id="ef3c8-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="ef3c8-434">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-434">String</span></span>|  
|<span data-ttu-id="ef3c8-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-435">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-436">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-436">String</span></span>|  
|<span data-ttu-id="ef3c8-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-437">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-438">Guid</span></span>|  
|<span data-ttu-id="ef3c8-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-439">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-440">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-440">Int64</span></span>|  
|<span data-ttu-id="ef3c8-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="ef3c8-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="ef3c8-442">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-442">Int64</span></span>|  
|<span data-ttu-id="ef3c8-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-444">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-444">Int64</span></span>|  
|<span data-ttu-id="ef3c8-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-445">IS_NULLABLE</span></span>|<span data-ttu-id="ef3c8-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-446">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-447">DATA_TYPE</span></span>|<span data-ttu-id="ef3c8-448">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-448">Int32</span></span>|  
|<span data-ttu-id="ef3c8-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-449">TYPE_GUID</span></span>|<span data-ttu-id="ef3c8-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-450">Guid</span></span>|  
|<span data-ttu-id="ef3c8-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="ef3c8-452">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-452">Int64</span></span>|  
|<span data-ttu-id="ef3c8-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="ef3c8-454">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-454">Int64</span></span>|  
|<span data-ttu-id="ef3c8-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="ef3c8-456">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-456">Int32</span></span>|  
|<span data-ttu-id="ef3c8-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="ef3c8-458">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-458">Int16</span></span>|  
|<span data-ttu-id="ef3c8-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-459">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-460">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-460">String</span></span>|  
|<span data-ttu-id="ef3c8-461">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-461">OVERLOAD</span></span>|<span data-ttu-id="ef3c8-462">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="ef3c8-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="ef3c8-463">Views</span></span>  
  
|<span data-ttu-id="ef3c8-464">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-464">ColumnName</span></span>|<span data-ttu-id="ef3c8-465">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-466">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-467">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-467">String</span></span>|  
|<span data-ttu-id="ef3c8-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-469">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-469">String</span></span>|  
|<span data-ttu-id="ef3c8-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-470">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-471">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-471">String</span></span>|  
|<span data-ttu-id="ef3c8-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="ef3c8-473">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-473">String</span></span>|  
|<span data-ttu-id="ef3c8-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-474">CHECK_OPTION</span></span>|<span data-ttu-id="ef3c8-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-475">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-476">IS_UPDATABLE</span></span>|<span data-ttu-id="ef3c8-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-477">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-478">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-479">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-479">String</span></span>|  
|<span data-ttu-id="ef3c8-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-480">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-481">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-482">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="ef3c8-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-484">Indexes</span></span>  
  
|<span data-ttu-id="ef3c8-485">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-485">ColumnName</span></span>|<span data-ttu-id="ef3c8-486">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-487">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-488">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-488">String</span></span>|  
|<span data-ttu-id="ef3c8-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-490">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-490">String</span></span>|  
|<span data-ttu-id="ef3c8-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-491">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-492">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-492">String</span></span>|  
|<span data-ttu-id="ef3c8-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-493">INDEX_CATALOG</span></span>|<span data-ttu-id="ef3c8-494">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-494">String</span></span>|  
|<span data-ttu-id="ef3c8-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="ef3c8-496">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-496">String</span></span>|  
|<span data-ttu-id="ef3c8-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-497">INDEX_NAME</span></span>|<span data-ttu-id="ef3c8-498">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-498">String</span></span>|  
|<span data-ttu-id="ef3c8-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-499">PRIMARY_KEY</span></span>|<span data-ttu-id="ef3c8-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-500">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-501">UNIQUE</span></span>|<span data-ttu-id="ef3c8-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-502">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-503">CLUSTERED</span></span>|<span data-ttu-id="ef3c8-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-504">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-505">TYP</span><span class="sxs-lookup"><span data-stu-id="ef3c8-505">TYPE</span></span>|<span data-ttu-id="ef3c8-506">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-506">Int32</span></span>|  
|<span data-ttu-id="ef3c8-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="ef3c8-507">FILL_FACTOR</span></span>|<span data-ttu-id="ef3c8-508">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-508">Int32</span></span>|  
|<span data-ttu-id="ef3c8-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-509">INITIAL_SIZE</span></span>|<span data-ttu-id="ef3c8-510">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-510">Int32</span></span>|  
|<span data-ttu-id="ef3c8-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="ef3c8-511">NULLS</span></span>|<span data-ttu-id="ef3c8-512">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-512">Int32</span></span>|  
|<span data-ttu-id="ef3c8-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="ef3c8-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-514">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-515">AUTO_UPDATE</span></span>|<span data-ttu-id="ef3c8-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-516">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-517">NULL_COLLATION</span></span>|<span data-ttu-id="ef3c8-518">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-518">Int32</span></span>|  
|<span data-ttu-id="ef3c8-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-520">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-520">Int64</span></span>|  
|<span data-ttu-id="ef3c8-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-521">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-522">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-522">String</span></span>|  
|<span data-ttu-id="ef3c8-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-523">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-524">Guid</span></span>|  
|<span data-ttu-id="ef3c8-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-525">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-526">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-526">Int64</span></span>|  
|<span data-ttu-id="ef3c8-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-527">COLLATION</span></span>|<span data-ttu-id="ef3c8-528">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-528">Int16</span></span>|  
|<span data-ttu-id="ef3c8-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="ef3c8-529">CARDINALITY</span></span>|<span data-ttu-id="ef3c8-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="ef3c8-530">Decimal</span></span>|  
|<span data-ttu-id="ef3c8-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-531">PAGES</span></span>|<span data-ttu-id="ef3c8-532">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-532">Int32</span></span>|  
|<span data-ttu-id="ef3c8-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-533">FILTER_CONDITION</span></span>|<span data-ttu-id="ef3c8-534">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-534">String</span></span>|  
|<span data-ttu-id="ef3c8-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-535">INTEGRATED</span></span>|<span data-ttu-id="ef3c8-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="ef3c8-537">Dostawca programu Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="ef3c8-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="ef3c8-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="ef3c8-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="ef3c8-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-539">Tables</span></span>  
  
-   <span data-ttu-id="ef3c8-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-540">Columns</span></span>  
  
-   <span data-ttu-id="ef3c8-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-541">Procedures</span></span>  
  
-   <span data-ttu-id="ef3c8-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="ef3c8-542">Views</span></span>  
  
-   <span data-ttu-id="ef3c8-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="ef3c8-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="ef3c8-544">Tables</span></span>  
  
|<span data-ttu-id="ef3c8-545">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-545">ColumnName</span></span>|<span data-ttu-id="ef3c8-546">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-547">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-548">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-548">String</span></span>|  
|<span data-ttu-id="ef3c8-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-550">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-550">String</span></span>|  
|<span data-ttu-id="ef3c8-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-551">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-552">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-552">String</span></span>|  
|<span data-ttu-id="ef3c8-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-553">TABLE_TYPE</span></span>|<span data-ttu-id="ef3c8-554">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-554">String</span></span>|  
|<span data-ttu-id="ef3c8-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-555">TABLE_GUID</span></span>|<span data-ttu-id="ef3c8-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-556">Guid</span></span>|  
|<span data-ttu-id="ef3c8-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-557">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-558">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-558">String</span></span>|  
|<span data-ttu-id="ef3c8-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-559">TABLE_PROPID</span></span>|<span data-ttu-id="ef3c8-560">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-560">Int64</span></span>|  
|<span data-ttu-id="ef3c8-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-561">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-562">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-563">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="ef3c8-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="ef3c8-565">Columns</span></span>  
  
|<span data-ttu-id="ef3c8-566">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-566">ColumnName</span></span>|<span data-ttu-id="ef3c8-567">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-568">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-569">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-569">String</span></span>|  
|<span data-ttu-id="ef3c8-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-571">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-571">String</span></span>|  
|<span data-ttu-id="ef3c8-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-572">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-573">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-573">String</span></span>|  
|<span data-ttu-id="ef3c8-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-574">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-575">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-575">String</span></span>|  
|<span data-ttu-id="ef3c8-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-576">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-577">Guid</span></span>|  
|<span data-ttu-id="ef3c8-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-578">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-579">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-579">Int64</span></span>|  
|<span data-ttu-id="ef3c8-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-581">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-581">Int64</span></span>|  
|<span data-ttu-id="ef3c8-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="ef3c8-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-583">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="ef3c8-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="ef3c8-585">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-585">String</span></span>|  
|<span data-ttu-id="ef3c8-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="ef3c8-587">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-587">Int64</span></span>|  
|<span data-ttu-id="ef3c8-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-588">IS_NULLABLE</span></span>|<span data-ttu-id="ef3c8-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-589">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-590">DATA_TYPE</span></span>|<span data-ttu-id="ef3c8-591">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-591">Int32</span></span>|  
|<span data-ttu-id="ef3c8-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-592">TYPE_GUID</span></span>|<span data-ttu-id="ef3c8-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-593">Guid</span></span>|  
|<span data-ttu-id="ef3c8-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="ef3c8-595">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-595">Int64</span></span>|  
|<span data-ttu-id="ef3c8-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="ef3c8-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="ef3c8-597">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-597">Int64</span></span>|  
|<span data-ttu-id="ef3c8-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="ef3c8-599">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-599">Int32</span></span>|  
|<span data-ttu-id="ef3c8-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="ef3c8-601">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-601">Int16</span></span>|  
|<span data-ttu-id="ef3c8-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="ef3c8-603">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-603">Int64</span></span>|  
|<span data-ttu-id="ef3c8-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="ef3c8-605">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-605">String</span></span>|  
|<span data-ttu-id="ef3c8-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="ef3c8-607">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-607">String</span></span>|  
|<span data-ttu-id="ef3c8-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="ef3c8-609">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-609">String</span></span>|  
|<span data-ttu-id="ef3c8-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="ef3c8-611">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-611">String</span></span>|  
|<span data-ttu-id="ef3c8-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="ef3c8-613">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-613">String</span></span>|  
|<span data-ttu-id="ef3c8-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-614">COLLATION_NAME</span></span>|<span data-ttu-id="ef3c8-615">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-615">String</span></span>|  
|<span data-ttu-id="ef3c8-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="ef3c8-617">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-617">String</span></span>|  
|<span data-ttu-id="ef3c8-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="ef3c8-619">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-619">String</span></span>|  
|<span data-ttu-id="ef3c8-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-620">DOMAIN_NAME</span></span>|<span data-ttu-id="ef3c8-621">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-621">String</span></span>|  
|<span data-ttu-id="ef3c8-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-622">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-623">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="ef3c8-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="ef3c8-624">Procedures</span></span>  
  
|<span data-ttu-id="ef3c8-625">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-625">ColumnName</span></span>|<span data-ttu-id="ef3c8-626">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="ef3c8-628">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-628">String</span></span>|  
|<span data-ttu-id="ef3c8-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-630">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-630">String</span></span>|  
|<span data-ttu-id="ef3c8-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="ef3c8-632">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-632">String</span></span>|  
|<span data-ttu-id="ef3c8-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="ef3c8-634">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-634">Int16</span></span>|  
|<span data-ttu-id="ef3c8-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="ef3c8-636">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-636">String</span></span>|  
|<span data-ttu-id="ef3c8-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-637">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-638">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-638">String</span></span>|  
|<span data-ttu-id="ef3c8-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-639">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-640">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-641">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="ef3c8-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="ef3c8-643">Views</span></span>  
  
|<span data-ttu-id="ef3c8-644">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-644">ColumnName</span></span>|<span data-ttu-id="ef3c8-645">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-646">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-647">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-647">String</span></span>|  
|<span data-ttu-id="ef3c8-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-649">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-649">String</span></span>|  
|<span data-ttu-id="ef3c8-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-650">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-651">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-651">String</span></span>|  
|<span data-ttu-id="ef3c8-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="ef3c8-653">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-653">String</span></span>|  
|<span data-ttu-id="ef3c8-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-654">CHECK_OPTION</span></span>|<span data-ttu-id="ef3c8-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-655">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-656">IS_UPDATABLE</span></span>|<span data-ttu-id="ef3c8-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-657">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="ef3c8-658">DESCRIPTION</span></span>|<span data-ttu-id="ef3c8-659">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-659">String</span></span>|  
|<span data-ttu-id="ef3c8-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-660">DATE_CREATED</span></span>|<span data-ttu-id="ef3c8-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-661">DateTime</span></span>|  
|<span data-ttu-id="ef3c8-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-662">DATE_MODIFIED</span></span>|<span data-ttu-id="ef3c8-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="ef3c8-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="ef3c8-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="ef3c8-664">Indexes</span></span>  
  
|<span data-ttu-id="ef3c8-665">Element columnName</span><span class="sxs-lookup"><span data-stu-id="ef3c8-665">ColumnName</span></span>|<span data-ttu-id="ef3c8-666">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ef3c8-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="ef3c8-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-667">TABLE_CATALOG</span></span>|<span data-ttu-id="ef3c8-668">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-668">String</span></span>|  
|<span data-ttu-id="ef3c8-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="ef3c8-670">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-670">String</span></span>|  
|<span data-ttu-id="ef3c8-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-671">TABLE_NAME</span></span>|<span data-ttu-id="ef3c8-672">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-672">String</span></span>|  
|<span data-ttu-id="ef3c8-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="ef3c8-673">INDEX_CATALOG</span></span>|<span data-ttu-id="ef3c8-674">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-674">String</span></span>|  
|<span data-ttu-id="ef3c8-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="ef3c8-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="ef3c8-676">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-676">String</span></span>|  
|<span data-ttu-id="ef3c8-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-677">INDEX_NAME</span></span>|<span data-ttu-id="ef3c8-678">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-678">String</span></span>|  
|<span data-ttu-id="ef3c8-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-679">PRIMARY_KEY</span></span>|<span data-ttu-id="ef3c8-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-680">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-681">UNIQUE</span></span>|<span data-ttu-id="ef3c8-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-682">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="ef3c8-683">CLUSTERED</span></span>|<span data-ttu-id="ef3c8-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-684">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-685">TYP</span><span class="sxs-lookup"><span data-stu-id="ef3c8-685">TYPE</span></span>|<span data-ttu-id="ef3c8-686">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-686">Int32</span></span>|  
|<span data-ttu-id="ef3c8-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="ef3c8-687">FILL_FACTOR</span></span>|<span data-ttu-id="ef3c8-688">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-688">Int32</span></span>|  
|<span data-ttu-id="ef3c8-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-689">INITIAL_SIZE</span></span>|<span data-ttu-id="ef3c8-690">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-690">Int32</span></span>|  
|<span data-ttu-id="ef3c8-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="ef3c8-691">NULLS</span></span>|<span data-ttu-id="ef3c8-692">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-692">Int32</span></span>|  
|<span data-ttu-id="ef3c8-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="ef3c8-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="ef3c8-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-694">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-695">AUTO_UPDATE</span></span>|<span data-ttu-id="ef3c8-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-696">Boolean</span></span>|  
|<span data-ttu-id="ef3c8-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-697">NULL_COLLATION</span></span>|<span data-ttu-id="ef3c8-698">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-698">Int32</span></span>|  
|<span data-ttu-id="ef3c8-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="ef3c8-700">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-700">Int64</span></span>|  
|<span data-ttu-id="ef3c8-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="ef3c8-701">COLUMN_NAME</span></span>|<span data-ttu-id="ef3c8-702">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-702">String</span></span>|  
|<span data-ttu-id="ef3c8-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-703">COLUMN_GUID</span></span>|<span data-ttu-id="ef3c8-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-704">Guid</span></span>|  
|<span data-ttu-id="ef3c8-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="ef3c8-705">COLUMN_PROPID</span></span>|<span data-ttu-id="ef3c8-706">Int64</span><span class="sxs-lookup"><span data-stu-id="ef3c8-706">Int64</span></span>|  
|<span data-ttu-id="ef3c8-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-707">COLLATION</span></span>|<span data-ttu-id="ef3c8-708">Int16</span><span class="sxs-lookup"><span data-stu-id="ef3c8-708">Int16</span></span>|  
|<span data-ttu-id="ef3c8-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="ef3c8-709">CARDINALITY</span></span>|<span data-ttu-id="ef3c8-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="ef3c8-710">Decimal</span></span>|  
|<span data-ttu-id="ef3c8-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="ef3c8-711">PAGES</span></span>|<span data-ttu-id="ef3c8-712">Int32</span><span class="sxs-lookup"><span data-stu-id="ef3c8-712">Int32</span></span>|  
|<span data-ttu-id="ef3c8-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="ef3c8-713">FILTER_CONDITION</span></span>|<span data-ttu-id="ef3c8-714">String</span><span class="sxs-lookup"><span data-stu-id="ef3c8-714">String</span></span>|  
|<span data-ttu-id="ef3c8-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="ef3c8-715">INTEGRATED</span></span>|<span data-ttu-id="ef3c8-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="ef3c8-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef3c8-717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef3c8-717">See Also</span></span>  
 [<span data-ttu-id="ef3c8-718">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="ef3c8-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
