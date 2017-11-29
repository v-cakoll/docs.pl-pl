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
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0478a-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="0478a-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="0478a-103">W tej sekcji omówiono obsługi kolekcji schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0478a-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0478a-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="0478a-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="0478a-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0478a-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0478a-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-106">Tables</span></span>  
  
-   <span data-ttu-id="0478a-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-107">Columns</span></span>  
  
-   <span data-ttu-id="0478a-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-108">Procedures</span></span>  
  
-   <span data-ttu-id="0478a-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0478a-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0478a-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="0478a-110">Catalog</span></span>  
  
-   <span data-ttu-id="0478a-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0478a-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-112">Tables</span></span>  
  
|<span data-ttu-id="0478a-113">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-113">ColumnName</span></span>|<span data-ttu-id="0478a-114">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-116">String</span><span class="sxs-lookup"><span data-stu-id="0478a-116">String</span></span>|  
|<span data-ttu-id="0478a-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-118">String</span><span class="sxs-lookup"><span data-stu-id="0478a-118">String</span></span>|  
|<span data-ttu-id="0478a-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-119">TABLE_NAME</span></span>|<span data-ttu-id="0478a-120">String</span><span class="sxs-lookup"><span data-stu-id="0478a-120">String</span></span>|  
|<span data-ttu-id="0478a-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-121">TABLE_TYPE</span></span>|<span data-ttu-id="0478a-122">String</span><span class="sxs-lookup"><span data-stu-id="0478a-122">String</span></span>|  
|<span data-ttu-id="0478a-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-123">TABLE_GUID</span></span>|<span data-ttu-id="0478a-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-124">Guid</span></span>|  
|<span data-ttu-id="0478a-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-125">DESCRIPTION</span></span>|<span data-ttu-id="0478a-126">String</span><span class="sxs-lookup"><span data-stu-id="0478a-126">String</span></span>|  
|<span data-ttu-id="0478a-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-127">TABLE_PROPID</span></span>|<span data-ttu-id="0478a-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-128">Int64</span></span>|  
|<span data-ttu-id="0478a-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-129">DATE_CREATED</span></span>|<span data-ttu-id="0478a-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-130">DateTime</span></span>|  
|<span data-ttu-id="0478a-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0478a-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-133">Columns</span></span>  
  
|<span data-ttu-id="0478a-134">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-134">ColumnName</span></span>|<span data-ttu-id="0478a-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-137">String</span><span class="sxs-lookup"><span data-stu-id="0478a-137">String</span></span>|  
|<span data-ttu-id="0478a-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-139">String</span><span class="sxs-lookup"><span data-stu-id="0478a-139">String</span></span>|  
|<span data-ttu-id="0478a-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-140">TABLE_NAME</span></span>|<span data-ttu-id="0478a-141">String</span><span class="sxs-lookup"><span data-stu-id="0478a-141">String</span></span>|  
|<span data-ttu-id="0478a-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-142">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-143">String</span><span class="sxs-lookup"><span data-stu-id="0478a-143">String</span></span>|  
|<span data-ttu-id="0478a-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-144">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-145">Guid</span></span>|  
|<span data-ttu-id="0478a-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-147">Int64</span></span>|  
|<span data-ttu-id="0478a-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-149">Int64</span></span>|  
|<span data-ttu-id="0478a-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0478a-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-151">Boolean</span></span>|  
|<span data-ttu-id="0478a-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0478a-153">String</span><span class="sxs-lookup"><span data-stu-id="0478a-153">String</span></span>|  
|<span data-ttu-id="0478a-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0478a-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0478a-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-155">Int64</span></span>|  
|<span data-ttu-id="0478a-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-156">IS_NULLABLE</span></span>|<span data-ttu-id="0478a-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-157">Boolean</span></span>|  
|<span data-ttu-id="0478a-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-158">DATA_TYPE</span></span>|<span data-ttu-id="0478a-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-159">Int32</span></span>|  
|<span data-ttu-id="0478a-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-160">TYPE_GUID</span></span>|<span data-ttu-id="0478a-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-161">Guid</span></span>|  
|<span data-ttu-id="0478a-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0478a-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-163">Int64</span></span>|  
|<span data-ttu-id="0478a-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0478a-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-165">Int64</span></span>|  
|<span data-ttu-id="0478a-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0478a-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-167">Int32</span></span>|  
|<span data-ttu-id="0478a-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0478a-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0478a-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-169">Int16</span></span>|  
|<span data-ttu-id="0478a-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0478a-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-171">Int64</span></span>|  
|<span data-ttu-id="0478a-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0478a-173">String</span><span class="sxs-lookup"><span data-stu-id="0478a-173">String</span></span>|  
|<span data-ttu-id="0478a-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0478a-175">String</span><span class="sxs-lookup"><span data-stu-id="0478a-175">String</span></span>|  
|<span data-ttu-id="0478a-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0478a-177">String</span><span class="sxs-lookup"><span data-stu-id="0478a-177">String</span></span>|  
|<span data-ttu-id="0478a-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0478a-179">String</span><span class="sxs-lookup"><span data-stu-id="0478a-179">String</span></span>|  
|<span data-ttu-id="0478a-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0478a-181">String</span><span class="sxs-lookup"><span data-stu-id="0478a-181">String</span></span>|  
|<span data-ttu-id="0478a-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-182">COLLATION_NAME</span></span>|<span data-ttu-id="0478a-183">String</span><span class="sxs-lookup"><span data-stu-id="0478a-183">String</span></span>|  
|<span data-ttu-id="0478a-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0478a-185">String</span><span class="sxs-lookup"><span data-stu-id="0478a-185">String</span></span>|  
|<span data-ttu-id="0478a-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0478a-187">String</span><span class="sxs-lookup"><span data-stu-id="0478a-187">String</span></span>|  
|<span data-ttu-id="0478a-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0478a-189">String</span><span class="sxs-lookup"><span data-stu-id="0478a-189">String</span></span>|  
|<span data-ttu-id="0478a-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-190">DESCRIPTION</span></span>|<span data-ttu-id="0478a-191">String</span><span class="sxs-lookup"><span data-stu-id="0478a-191">String</span></span>|  
|<span data-ttu-id="0478a-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0478a-192">COLUMN_LCID</span></span>|<span data-ttu-id="0478a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-193">Int32</span></span>|  
|<span data-ttu-id="0478a-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0478a-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0478a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-195">Int32</span></span>|  
|<span data-ttu-id="0478a-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0478a-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0478a-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-197">Int32</span></span>|  
|<span data-ttu-id="0478a-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0478a-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0478a-199">Byte]</span><span class="sxs-lookup"><span data-stu-id="0478a-199">Byte[]</span></span>|  
|<span data-ttu-id="0478a-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0478a-200">IS_COMPUTED</span></span>|<span data-ttu-id="0478a-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0478a-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-202">Procedures</span></span>  
  
|<span data-ttu-id="0478a-203">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-203">ColumnName</span></span>|<span data-ttu-id="0478a-204">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0478a-206">String</span><span class="sxs-lookup"><span data-stu-id="0478a-206">String</span></span>|  
|<span data-ttu-id="0478a-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0478a-208">String</span><span class="sxs-lookup"><span data-stu-id="0478a-208">String</span></span>|  
|<span data-ttu-id="0478a-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0478a-210">String</span><span class="sxs-lookup"><span data-stu-id="0478a-210">String</span></span>|  
|<span data-ttu-id="0478a-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0478a-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-212">Int16</span></span>|  
|<span data-ttu-id="0478a-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0478a-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0478a-214">String</span><span class="sxs-lookup"><span data-stu-id="0478a-214">String</span></span>|  
|<span data-ttu-id="0478a-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-215">DESCRIPTION</span></span>|<span data-ttu-id="0478a-216">String</span><span class="sxs-lookup"><span data-stu-id="0478a-216">String</span></span>|  
|<span data-ttu-id="0478a-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-217">DATE_CREATED</span></span>|<span data-ttu-id="0478a-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-218">DateTime</span></span>|  
|<span data-ttu-id="0478a-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0478a-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0478a-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0478a-222">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-222">ColumnName</span></span>|<span data-ttu-id="0478a-223">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0478a-225">String</span><span class="sxs-lookup"><span data-stu-id="0478a-225">String</span></span>|  
|<span data-ttu-id="0478a-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0478a-227">String</span><span class="sxs-lookup"><span data-stu-id="0478a-227">String</span></span>|  
|<span data-ttu-id="0478a-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0478a-229">String</span><span class="sxs-lookup"><span data-stu-id="0478a-229">String</span></span>|  
|<span data-ttu-id="0478a-230">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="0478a-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0478a-231">String</span><span class="sxs-lookup"><span data-stu-id="0478a-231">String</span></span>|  
|<span data-ttu-id="0478a-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-233">Int32</span></span>|  
|<span data-ttu-id="0478a-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="0478a-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0478a-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-235">Int32</span></span>|  
|<span data-ttu-id="0478a-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0478a-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-237">Boolean</span></span>|  
|<span data-ttu-id="0478a-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0478a-239">String</span><span class="sxs-lookup"><span data-stu-id="0478a-239">String</span></span>|  
|<span data-ttu-id="0478a-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-240">IS_NULLABLE</span></span>|<span data-ttu-id="0478a-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-241">Boolean</span></span>|  
|<span data-ttu-id="0478a-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-242">DATA_TYPE</span></span>|<span data-ttu-id="0478a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-243">Int32</span></span>|  
|<span data-ttu-id="0478a-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0478a-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-245">Int64</span></span>|  
|<span data-ttu-id="0478a-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0478a-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-247">Int64</span></span>|  
|<span data-ttu-id="0478a-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0478a-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-249">Int32</span></span>|  
|<span data-ttu-id="0478a-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0478a-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0478a-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-251">Int16</span></span>|  
|<span data-ttu-id="0478a-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-252">DESCRIPTION</span></span>|<span data-ttu-id="0478a-253">String</span><span class="sxs-lookup"><span data-stu-id="0478a-253">String</span></span>|  
|<span data-ttu-id="0478a-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-254">TYPE_NAME</span></span>|<span data-ttu-id="0478a-255">String</span><span class="sxs-lookup"><span data-stu-id="0478a-255">String</span></span>|  
|<span data-ttu-id="0478a-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0478a-257">String</span><span class="sxs-lookup"><span data-stu-id="0478a-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0478a-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="0478a-258">Catalog</span></span>  
  
|<span data-ttu-id="0478a-259">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-259">ColumnName</span></span>|<span data-ttu-id="0478a-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-261">CATALOG_NAME</span></span>|<span data-ttu-id="0478a-262">String</span><span class="sxs-lookup"><span data-stu-id="0478a-262">String</span></span>|  
|<span data-ttu-id="0478a-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-263">DESCRIPTION</span></span>|<span data-ttu-id="0478a-264">String</span><span class="sxs-lookup"><span data-stu-id="0478a-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0478a-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-265">Indexes</span></span>  
  
|<span data-ttu-id="0478a-266">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-266">ColumnName</span></span>|<span data-ttu-id="0478a-267">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-269">String</span><span class="sxs-lookup"><span data-stu-id="0478a-269">String</span></span>|  
|<span data-ttu-id="0478a-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-271">String</span><span class="sxs-lookup"><span data-stu-id="0478a-271">String</span></span>|  
|<span data-ttu-id="0478a-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-272">TABLE_NAME</span></span>|<span data-ttu-id="0478a-273">String</span><span class="sxs-lookup"><span data-stu-id="0478a-273">String</span></span>|  
|<span data-ttu-id="0478a-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0478a-275">String</span><span class="sxs-lookup"><span data-stu-id="0478a-275">String</span></span>|  
|<span data-ttu-id="0478a-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0478a-277">String</span><span class="sxs-lookup"><span data-stu-id="0478a-277">String</span></span>|  
|<span data-ttu-id="0478a-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-278">INDEX_NAME</span></span>|<span data-ttu-id="0478a-279">String</span><span class="sxs-lookup"><span data-stu-id="0478a-279">String</span></span>|  
|<span data-ttu-id="0478a-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0478a-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0478a-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-281">Boolean</span></span>|  
|<span data-ttu-id="0478a-282">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="0478a-282">UNIQUE</span></span>|<span data-ttu-id="0478a-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-283">Boolean</span></span>|  
|<span data-ttu-id="0478a-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0478a-284">CLUSTERED</span></span>|<span data-ttu-id="0478a-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-285">Boolean</span></span>|  
|<span data-ttu-id="0478a-286">TYP</span><span class="sxs-lookup"><span data-stu-id="0478a-286">TYPE</span></span>|<span data-ttu-id="0478a-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-287">Int32</span></span>|  
|<span data-ttu-id="0478a-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0478a-288">FILL_FACTOR</span></span>|<span data-ttu-id="0478a-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-289">Int32</span></span>|  
|<span data-ttu-id="0478a-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0478a-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0478a-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-291">Int32</span></span>|  
|<span data-ttu-id="0478a-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0478a-292">NULLS</span></span>|<span data-ttu-id="0478a-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-293">Int32</span></span>|  
|<span data-ttu-id="0478a-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0478a-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0478a-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-295">Boolean</span></span>|  
|<span data-ttu-id="0478a-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0478a-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0478a-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-297">Boolean</span></span>|  
|<span data-ttu-id="0478a-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0478a-298">NULL_COLLATION</span></span>|<span data-ttu-id="0478a-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-299">Int32</span></span>|  
|<span data-ttu-id="0478a-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-301">Int64</span></span>|  
|<span data-ttu-id="0478a-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-302">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-303">String</span><span class="sxs-lookup"><span data-stu-id="0478a-303">String</span></span>|  
|<span data-ttu-id="0478a-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-304">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-305">Guid</span></span>|  
|<span data-ttu-id="0478a-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-307">Int64</span></span>|  
|<span data-ttu-id="0478a-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0478a-308">COLLATION</span></span>|<span data-ttu-id="0478a-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-309">Int16</span></span>|  
|<span data-ttu-id="0478a-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0478a-310">CARDINALITY</span></span>|<span data-ttu-id="0478a-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0478a-311">Decimal</span></span>|  
|<span data-ttu-id="0478a-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="0478a-312">PAGES</span></span>|<span data-ttu-id="0478a-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-313">Int32</span></span>|  
|<span data-ttu-id="0478a-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0478a-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0478a-315">String</span><span class="sxs-lookup"><span data-stu-id="0478a-315">String</span></span>|  
|<span data-ttu-id="0478a-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0478a-316">INTEGRATED</span></span>|<span data-ttu-id="0478a-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0478a-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="0478a-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="0478a-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0478a-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0478a-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-320">Tables</span></span>  
  
-   <span data-ttu-id="0478a-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-321">Columns</span></span>  
  
-   <span data-ttu-id="0478a-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-322">Procedures</span></span>  
  
-   <span data-ttu-id="0478a-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0478a-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0478a-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0478a-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0478a-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="0478a-325">Views</span></span>  
  
-   <span data-ttu-id="0478a-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0478a-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-327">Tables</span></span>  
  
|<span data-ttu-id="0478a-328">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-328">ColumnName</span></span>|<span data-ttu-id="0478a-329">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-331">String</span><span class="sxs-lookup"><span data-stu-id="0478a-331">String</span></span>|  
|<span data-ttu-id="0478a-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-333">String</span><span class="sxs-lookup"><span data-stu-id="0478a-333">String</span></span>|  
|<span data-ttu-id="0478a-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-334">TABLE_NAME</span></span>|<span data-ttu-id="0478a-335">String</span><span class="sxs-lookup"><span data-stu-id="0478a-335">String</span></span>|  
|<span data-ttu-id="0478a-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-336">TABLE_TYPE</span></span>|<span data-ttu-id="0478a-337">String</span><span class="sxs-lookup"><span data-stu-id="0478a-337">String</span></span>|  
|<span data-ttu-id="0478a-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-338">TABLE_GUID</span></span>|<span data-ttu-id="0478a-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-339">Guid</span></span>|  
|<span data-ttu-id="0478a-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-340">DESCRIPTION</span></span>|<span data-ttu-id="0478a-341">String</span><span class="sxs-lookup"><span data-stu-id="0478a-341">String</span></span>|  
|<span data-ttu-id="0478a-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-342">TABLE_PROPID</span></span>|<span data-ttu-id="0478a-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-343">Int64</span></span>|  
|<span data-ttu-id="0478a-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-344">DATE_CREATED</span></span>|<span data-ttu-id="0478a-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-345">DateTime</span></span>|  
|<span data-ttu-id="0478a-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0478a-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-348">Columns</span></span>  
  
|<span data-ttu-id="0478a-349">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-349">ColumnName</span></span>|<span data-ttu-id="0478a-350">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-352">String</span><span class="sxs-lookup"><span data-stu-id="0478a-352">String</span></span>|  
|<span data-ttu-id="0478a-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-354">String</span><span class="sxs-lookup"><span data-stu-id="0478a-354">String</span></span>|  
|<span data-ttu-id="0478a-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-355">TABLE_NAME</span></span>|<span data-ttu-id="0478a-356">String</span><span class="sxs-lookup"><span data-stu-id="0478a-356">String</span></span>|  
|<span data-ttu-id="0478a-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-357">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-358">String</span><span class="sxs-lookup"><span data-stu-id="0478a-358">String</span></span>|  
|<span data-ttu-id="0478a-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-359">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-360">Guid</span></span>|  
|<span data-ttu-id="0478a-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-362">Int64</span></span>|  
|<span data-ttu-id="0478a-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-364">Int64</span></span>|  
|<span data-ttu-id="0478a-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0478a-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-366">Boolean</span></span>|  
|<span data-ttu-id="0478a-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0478a-368">String</span><span class="sxs-lookup"><span data-stu-id="0478a-368">String</span></span>|  
|<span data-ttu-id="0478a-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0478a-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0478a-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-370">Int64</span></span>|  
|<span data-ttu-id="0478a-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-371">IS_NULLABLE</span></span>|<span data-ttu-id="0478a-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-372">Boolean</span></span>|  
|<span data-ttu-id="0478a-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-373">DATA_TYPE</span></span>|<span data-ttu-id="0478a-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-374">Int32</span></span>|  
|<span data-ttu-id="0478a-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-375">TYPE_GUID</span></span>|<span data-ttu-id="0478a-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-376">Guid</span></span>|  
|<span data-ttu-id="0478a-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0478a-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-378">Int64</span></span>|  
|<span data-ttu-id="0478a-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0478a-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-380">Int64</span></span>|  
|<span data-ttu-id="0478a-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0478a-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-382">Int32</span></span>|  
|<span data-ttu-id="0478a-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0478a-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0478a-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-384">Int16</span></span>|  
|<span data-ttu-id="0478a-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0478a-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-386">Int64</span></span>|  
|<span data-ttu-id="0478a-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0478a-388">String</span><span class="sxs-lookup"><span data-stu-id="0478a-388">String</span></span>|  
|<span data-ttu-id="0478a-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0478a-390">String</span><span class="sxs-lookup"><span data-stu-id="0478a-390">String</span></span>|  
|<span data-ttu-id="0478a-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0478a-392">String</span><span class="sxs-lookup"><span data-stu-id="0478a-392">String</span></span>|  
|<span data-ttu-id="0478a-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0478a-394">String</span><span class="sxs-lookup"><span data-stu-id="0478a-394">String</span></span>|  
|<span data-ttu-id="0478a-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0478a-396">String</span><span class="sxs-lookup"><span data-stu-id="0478a-396">String</span></span>|  
|<span data-ttu-id="0478a-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-397">COLLATION_NAME</span></span>|<span data-ttu-id="0478a-398">String</span><span class="sxs-lookup"><span data-stu-id="0478a-398">String</span></span>|  
|<span data-ttu-id="0478a-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0478a-400">String</span><span class="sxs-lookup"><span data-stu-id="0478a-400">String</span></span>|  
|<span data-ttu-id="0478a-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0478a-402">String</span><span class="sxs-lookup"><span data-stu-id="0478a-402">String</span></span>|  
|<span data-ttu-id="0478a-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0478a-404">String</span><span class="sxs-lookup"><span data-stu-id="0478a-404">String</span></span>|  
|<span data-ttu-id="0478a-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-405">DESCRIPTION</span></span>|<span data-ttu-id="0478a-406">String</span><span class="sxs-lookup"><span data-stu-id="0478a-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0478a-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-407">Procedures</span></span>  
  
|<span data-ttu-id="0478a-408">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-408">ColumnName</span></span>|<span data-ttu-id="0478a-409">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0478a-411">String</span><span class="sxs-lookup"><span data-stu-id="0478a-411">String</span></span>|  
|<span data-ttu-id="0478a-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0478a-413">String</span><span class="sxs-lookup"><span data-stu-id="0478a-413">String</span></span>|  
|<span data-ttu-id="0478a-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0478a-415">String</span><span class="sxs-lookup"><span data-stu-id="0478a-415">String</span></span>|  
|<span data-ttu-id="0478a-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0478a-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-417">Int16</span></span>|  
|<span data-ttu-id="0478a-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0478a-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0478a-419">String</span><span class="sxs-lookup"><span data-stu-id="0478a-419">String</span></span>|  
|<span data-ttu-id="0478a-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-420">DESCRIPTION</span></span>|<span data-ttu-id="0478a-421">String</span><span class="sxs-lookup"><span data-stu-id="0478a-421">String</span></span>|  
|<span data-ttu-id="0478a-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-422">DATE_CREATED</span></span>|<span data-ttu-id="0478a-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-423">DateTime</span></span>|  
|<span data-ttu-id="0478a-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0478a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0478a-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0478a-427">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-427">ColumnName</span></span>|<span data-ttu-id="0478a-428">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0478a-430">String</span><span class="sxs-lookup"><span data-stu-id="0478a-430">String</span></span>|  
|<span data-ttu-id="0478a-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0478a-432">String</span><span class="sxs-lookup"><span data-stu-id="0478a-432">String</span></span>|  
|<span data-ttu-id="0478a-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0478a-434">String</span><span class="sxs-lookup"><span data-stu-id="0478a-434">String</span></span>|  
|<span data-ttu-id="0478a-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-435">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-436">String</span><span class="sxs-lookup"><span data-stu-id="0478a-436">String</span></span>|  
|<span data-ttu-id="0478a-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-437">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-438">Guid</span></span>|  
|<span data-ttu-id="0478a-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-440">Int64</span></span>|  
|<span data-ttu-id="0478a-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0478a-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0478a-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-442">Int64</span></span>|  
|<span data-ttu-id="0478a-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-444">Int64</span></span>|  
|<span data-ttu-id="0478a-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-445">IS_NULLABLE</span></span>|<span data-ttu-id="0478a-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-446">Boolean</span></span>|  
|<span data-ttu-id="0478a-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-447">DATA_TYPE</span></span>|<span data-ttu-id="0478a-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-448">Int32</span></span>|  
|<span data-ttu-id="0478a-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-449">TYPE_GUID</span></span>|<span data-ttu-id="0478a-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-450">Guid</span></span>|  
|<span data-ttu-id="0478a-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0478a-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-452">Int64</span></span>|  
|<span data-ttu-id="0478a-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0478a-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-454">Int64</span></span>|  
|<span data-ttu-id="0478a-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0478a-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-456">Int32</span></span>|  
|<span data-ttu-id="0478a-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0478a-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0478a-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-458">Int16</span></span>|  
|<span data-ttu-id="0478a-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-459">DESCRIPTION</span></span>|<span data-ttu-id="0478a-460">String</span><span class="sxs-lookup"><span data-stu-id="0478a-460">String</span></span>|  
|<span data-ttu-id="0478a-461">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="0478a-461">OVERLOAD</span></span>|<span data-ttu-id="0478a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0478a-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="0478a-463">Views</span></span>  
  
|<span data-ttu-id="0478a-464">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-464">ColumnName</span></span>|<span data-ttu-id="0478a-465">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-467">String</span><span class="sxs-lookup"><span data-stu-id="0478a-467">String</span></span>|  
|<span data-ttu-id="0478a-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-469">String</span><span class="sxs-lookup"><span data-stu-id="0478a-469">String</span></span>|  
|<span data-ttu-id="0478a-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-470">TABLE_NAME</span></span>|<span data-ttu-id="0478a-471">String</span><span class="sxs-lookup"><span data-stu-id="0478a-471">String</span></span>|  
|<span data-ttu-id="0478a-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0478a-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0478a-473">String</span><span class="sxs-lookup"><span data-stu-id="0478a-473">String</span></span>|  
|<span data-ttu-id="0478a-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0478a-474">CHECK_OPTION</span></span>|<span data-ttu-id="0478a-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-475">Boolean</span></span>|  
|<span data-ttu-id="0478a-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0478a-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-477">Boolean</span></span>|  
|<span data-ttu-id="0478a-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-478">DESCRIPTION</span></span>|<span data-ttu-id="0478a-479">String</span><span class="sxs-lookup"><span data-stu-id="0478a-479">String</span></span>|  
|<span data-ttu-id="0478a-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-480">DATE_CREATED</span></span>|<span data-ttu-id="0478a-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-481">DateTime</span></span>|  
|<span data-ttu-id="0478a-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0478a-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-484">Indexes</span></span>  
  
|<span data-ttu-id="0478a-485">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-485">ColumnName</span></span>|<span data-ttu-id="0478a-486">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-488">String</span><span class="sxs-lookup"><span data-stu-id="0478a-488">String</span></span>|  
|<span data-ttu-id="0478a-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-490">String</span><span class="sxs-lookup"><span data-stu-id="0478a-490">String</span></span>|  
|<span data-ttu-id="0478a-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-491">TABLE_NAME</span></span>|<span data-ttu-id="0478a-492">String</span><span class="sxs-lookup"><span data-stu-id="0478a-492">String</span></span>|  
|<span data-ttu-id="0478a-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0478a-494">String</span><span class="sxs-lookup"><span data-stu-id="0478a-494">String</span></span>|  
|<span data-ttu-id="0478a-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0478a-496">String</span><span class="sxs-lookup"><span data-stu-id="0478a-496">String</span></span>|  
|<span data-ttu-id="0478a-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-497">INDEX_NAME</span></span>|<span data-ttu-id="0478a-498">String</span><span class="sxs-lookup"><span data-stu-id="0478a-498">String</span></span>|  
|<span data-ttu-id="0478a-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0478a-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0478a-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-500">Boolean</span></span>|  
|<span data-ttu-id="0478a-501">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="0478a-501">UNIQUE</span></span>|<span data-ttu-id="0478a-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-502">Boolean</span></span>|  
|<span data-ttu-id="0478a-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0478a-503">CLUSTERED</span></span>|<span data-ttu-id="0478a-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-504">Boolean</span></span>|  
|<span data-ttu-id="0478a-505">TYP</span><span class="sxs-lookup"><span data-stu-id="0478a-505">TYPE</span></span>|<span data-ttu-id="0478a-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-506">Int32</span></span>|  
|<span data-ttu-id="0478a-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0478a-507">FILL_FACTOR</span></span>|<span data-ttu-id="0478a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-508">Int32</span></span>|  
|<span data-ttu-id="0478a-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0478a-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0478a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-510">Int32</span></span>|  
|<span data-ttu-id="0478a-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0478a-511">NULLS</span></span>|<span data-ttu-id="0478a-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-512">Int32</span></span>|  
|<span data-ttu-id="0478a-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0478a-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0478a-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-514">Boolean</span></span>|  
|<span data-ttu-id="0478a-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0478a-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0478a-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-516">Boolean</span></span>|  
|<span data-ttu-id="0478a-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0478a-517">NULL_COLLATION</span></span>|<span data-ttu-id="0478a-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-518">Int32</span></span>|  
|<span data-ttu-id="0478a-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-520">Int64</span></span>|  
|<span data-ttu-id="0478a-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-521">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-522">String</span><span class="sxs-lookup"><span data-stu-id="0478a-522">String</span></span>|  
|<span data-ttu-id="0478a-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-523">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-524">Guid</span></span>|  
|<span data-ttu-id="0478a-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-526">Int64</span></span>|  
|<span data-ttu-id="0478a-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0478a-527">COLLATION</span></span>|<span data-ttu-id="0478a-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-528">Int16</span></span>|  
|<span data-ttu-id="0478a-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0478a-529">CARDINALITY</span></span>|<span data-ttu-id="0478a-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0478a-530">Decimal</span></span>|  
|<span data-ttu-id="0478a-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="0478a-531">PAGES</span></span>|<span data-ttu-id="0478a-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-532">Int32</span></span>|  
|<span data-ttu-id="0478a-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0478a-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0478a-534">String</span><span class="sxs-lookup"><span data-stu-id="0478a-534">String</span></span>|  
|<span data-ttu-id="0478a-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0478a-535">INTEGRATED</span></span>|<span data-ttu-id="0478a-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0478a-537">Dostawca programu Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="0478a-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="0478a-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0478a-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0478a-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-539">Tables</span></span>  
  
-   <span data-ttu-id="0478a-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-540">Columns</span></span>  
  
-   <span data-ttu-id="0478a-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-541">Procedures</span></span>  
  
-   <span data-ttu-id="0478a-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="0478a-542">Views</span></span>  
  
-   <span data-ttu-id="0478a-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0478a-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="0478a-544">Tables</span></span>  
  
|<span data-ttu-id="0478a-545">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-545">ColumnName</span></span>|<span data-ttu-id="0478a-546">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-548">String</span><span class="sxs-lookup"><span data-stu-id="0478a-548">String</span></span>|  
|<span data-ttu-id="0478a-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-550">String</span><span class="sxs-lookup"><span data-stu-id="0478a-550">String</span></span>|  
|<span data-ttu-id="0478a-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-551">TABLE_NAME</span></span>|<span data-ttu-id="0478a-552">String</span><span class="sxs-lookup"><span data-stu-id="0478a-552">String</span></span>|  
|<span data-ttu-id="0478a-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-553">TABLE_TYPE</span></span>|<span data-ttu-id="0478a-554">String</span><span class="sxs-lookup"><span data-stu-id="0478a-554">String</span></span>|  
|<span data-ttu-id="0478a-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-555">TABLE_GUID</span></span>|<span data-ttu-id="0478a-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-556">Guid</span></span>|  
|<span data-ttu-id="0478a-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-557">DESCRIPTION</span></span>|<span data-ttu-id="0478a-558">String</span><span class="sxs-lookup"><span data-stu-id="0478a-558">String</span></span>|  
|<span data-ttu-id="0478a-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-559">TABLE_PROPID</span></span>|<span data-ttu-id="0478a-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-560">Int64</span></span>|  
|<span data-ttu-id="0478a-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-561">DATE_CREATED</span></span>|<span data-ttu-id="0478a-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-562">DateTime</span></span>|  
|<span data-ttu-id="0478a-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0478a-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0478a-565">Columns</span></span>  
  
|<span data-ttu-id="0478a-566">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-566">ColumnName</span></span>|<span data-ttu-id="0478a-567">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-569">String</span><span class="sxs-lookup"><span data-stu-id="0478a-569">String</span></span>|  
|<span data-ttu-id="0478a-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-571">String</span><span class="sxs-lookup"><span data-stu-id="0478a-571">String</span></span>|  
|<span data-ttu-id="0478a-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-572">TABLE_NAME</span></span>|<span data-ttu-id="0478a-573">String</span><span class="sxs-lookup"><span data-stu-id="0478a-573">String</span></span>|  
|<span data-ttu-id="0478a-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-574">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-575">String</span><span class="sxs-lookup"><span data-stu-id="0478a-575">String</span></span>|  
|<span data-ttu-id="0478a-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-576">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-577">Guid</span></span>|  
|<span data-ttu-id="0478a-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-579">Int64</span></span>|  
|<span data-ttu-id="0478a-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-581">Int64</span></span>|  
|<span data-ttu-id="0478a-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0478a-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-583">Boolean</span></span>|  
|<span data-ttu-id="0478a-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0478a-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0478a-585">String</span><span class="sxs-lookup"><span data-stu-id="0478a-585">String</span></span>|  
|<span data-ttu-id="0478a-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0478a-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0478a-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-587">Int64</span></span>|  
|<span data-ttu-id="0478a-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-588">IS_NULLABLE</span></span>|<span data-ttu-id="0478a-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-589">Boolean</span></span>|  
|<span data-ttu-id="0478a-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-590">DATA_TYPE</span></span>|<span data-ttu-id="0478a-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-591">Int32</span></span>|  
|<span data-ttu-id="0478a-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-592">TYPE_GUID</span></span>|<span data-ttu-id="0478a-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-593">Guid</span></span>|  
|<span data-ttu-id="0478a-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0478a-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-595">Int64</span></span>|  
|<span data-ttu-id="0478a-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0478a-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0478a-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-597">Int64</span></span>|  
|<span data-ttu-id="0478a-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0478a-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-599">Int32</span></span>|  
|<span data-ttu-id="0478a-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0478a-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0478a-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-601">Int16</span></span>|  
|<span data-ttu-id="0478a-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0478a-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0478a-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-603">Int64</span></span>|  
|<span data-ttu-id="0478a-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0478a-605">String</span><span class="sxs-lookup"><span data-stu-id="0478a-605">String</span></span>|  
|<span data-ttu-id="0478a-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0478a-607">String</span><span class="sxs-lookup"><span data-stu-id="0478a-607">String</span></span>|  
|<span data-ttu-id="0478a-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0478a-609">String</span><span class="sxs-lookup"><span data-stu-id="0478a-609">String</span></span>|  
|<span data-ttu-id="0478a-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0478a-611">String</span><span class="sxs-lookup"><span data-stu-id="0478a-611">String</span></span>|  
|<span data-ttu-id="0478a-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0478a-613">String</span><span class="sxs-lookup"><span data-stu-id="0478a-613">String</span></span>|  
|<span data-ttu-id="0478a-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-614">COLLATION_NAME</span></span>|<span data-ttu-id="0478a-615">String</span><span class="sxs-lookup"><span data-stu-id="0478a-615">String</span></span>|  
|<span data-ttu-id="0478a-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0478a-617">String</span><span class="sxs-lookup"><span data-stu-id="0478a-617">String</span></span>|  
|<span data-ttu-id="0478a-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0478a-619">String</span><span class="sxs-lookup"><span data-stu-id="0478a-619">String</span></span>|  
|<span data-ttu-id="0478a-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0478a-621">String</span><span class="sxs-lookup"><span data-stu-id="0478a-621">String</span></span>|  
|<span data-ttu-id="0478a-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-622">DESCRIPTION</span></span>|<span data-ttu-id="0478a-623">String</span><span class="sxs-lookup"><span data-stu-id="0478a-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0478a-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="0478a-624">Procedures</span></span>  
  
|<span data-ttu-id="0478a-625">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-625">ColumnName</span></span>|<span data-ttu-id="0478a-626">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0478a-628">String</span><span class="sxs-lookup"><span data-stu-id="0478a-628">String</span></span>|  
|<span data-ttu-id="0478a-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0478a-630">String</span><span class="sxs-lookup"><span data-stu-id="0478a-630">String</span></span>|  
|<span data-ttu-id="0478a-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0478a-632">String</span><span class="sxs-lookup"><span data-stu-id="0478a-632">String</span></span>|  
|<span data-ttu-id="0478a-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0478a-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0478a-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-634">Int16</span></span>|  
|<span data-ttu-id="0478a-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0478a-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0478a-636">String</span><span class="sxs-lookup"><span data-stu-id="0478a-636">String</span></span>|  
|<span data-ttu-id="0478a-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-637">DESCRIPTION</span></span>|<span data-ttu-id="0478a-638">String</span><span class="sxs-lookup"><span data-stu-id="0478a-638">String</span></span>|  
|<span data-ttu-id="0478a-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-639">DATE_CREATED</span></span>|<span data-ttu-id="0478a-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-640">DateTime</span></span>|  
|<span data-ttu-id="0478a-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0478a-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="0478a-643">Views</span></span>  
  
|<span data-ttu-id="0478a-644">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-644">ColumnName</span></span>|<span data-ttu-id="0478a-645">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-647">String</span><span class="sxs-lookup"><span data-stu-id="0478a-647">String</span></span>|  
|<span data-ttu-id="0478a-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-649">String</span><span class="sxs-lookup"><span data-stu-id="0478a-649">String</span></span>|  
|<span data-ttu-id="0478a-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-650">TABLE_NAME</span></span>|<span data-ttu-id="0478a-651">String</span><span class="sxs-lookup"><span data-stu-id="0478a-651">String</span></span>|  
|<span data-ttu-id="0478a-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0478a-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0478a-653">String</span><span class="sxs-lookup"><span data-stu-id="0478a-653">String</span></span>|  
|<span data-ttu-id="0478a-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0478a-654">CHECK_OPTION</span></span>|<span data-ttu-id="0478a-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-655">Boolean</span></span>|  
|<span data-ttu-id="0478a-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0478a-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0478a-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-657">Boolean</span></span>|  
|<span data-ttu-id="0478a-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0478a-658">DESCRIPTION</span></span>|<span data-ttu-id="0478a-659">String</span><span class="sxs-lookup"><span data-stu-id="0478a-659">String</span></span>|  
|<span data-ttu-id="0478a-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0478a-660">DATE_CREATED</span></span>|<span data-ttu-id="0478a-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-661">DateTime</span></span>|  
|<span data-ttu-id="0478a-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0478a-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0478a-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0478a-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0478a-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0478a-664">Indexes</span></span>  
  
|<span data-ttu-id="0478a-665">Element columnName</span><span class="sxs-lookup"><span data-stu-id="0478a-665">ColumnName</span></span>|<span data-ttu-id="0478a-666">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0478a-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0478a-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0478a-668">String</span><span class="sxs-lookup"><span data-stu-id="0478a-668">String</span></span>|  
|<span data-ttu-id="0478a-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0478a-670">String</span><span class="sxs-lookup"><span data-stu-id="0478a-670">String</span></span>|  
|<span data-ttu-id="0478a-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-671">TABLE_NAME</span></span>|<span data-ttu-id="0478a-672">String</span><span class="sxs-lookup"><span data-stu-id="0478a-672">String</span></span>|  
|<span data-ttu-id="0478a-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0478a-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0478a-674">String</span><span class="sxs-lookup"><span data-stu-id="0478a-674">String</span></span>|  
|<span data-ttu-id="0478a-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0478a-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0478a-676">String</span><span class="sxs-lookup"><span data-stu-id="0478a-676">String</span></span>|  
|<span data-ttu-id="0478a-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-677">INDEX_NAME</span></span>|<span data-ttu-id="0478a-678">String</span><span class="sxs-lookup"><span data-stu-id="0478a-678">String</span></span>|  
|<span data-ttu-id="0478a-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0478a-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0478a-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-680">Boolean</span></span>|  
|<span data-ttu-id="0478a-681">UNIKATOWE</span><span class="sxs-lookup"><span data-stu-id="0478a-681">UNIQUE</span></span>|<span data-ttu-id="0478a-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-682">Boolean</span></span>|  
|<span data-ttu-id="0478a-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0478a-683">CLUSTERED</span></span>|<span data-ttu-id="0478a-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-684">Boolean</span></span>|  
|<span data-ttu-id="0478a-685">TYP</span><span class="sxs-lookup"><span data-stu-id="0478a-685">TYPE</span></span>|<span data-ttu-id="0478a-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-686">Int32</span></span>|  
|<span data-ttu-id="0478a-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0478a-687">FILL_FACTOR</span></span>|<span data-ttu-id="0478a-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-688">Int32</span></span>|  
|<span data-ttu-id="0478a-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0478a-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0478a-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-690">Int32</span></span>|  
|<span data-ttu-id="0478a-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0478a-691">NULLS</span></span>|<span data-ttu-id="0478a-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-692">Int32</span></span>|  
|<span data-ttu-id="0478a-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0478a-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0478a-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-694">Boolean</span></span>|  
|<span data-ttu-id="0478a-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0478a-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0478a-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-696">Boolean</span></span>|  
|<span data-ttu-id="0478a-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0478a-697">NULL_COLLATION</span></span>|<span data-ttu-id="0478a-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-698">Int32</span></span>|  
|<span data-ttu-id="0478a-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0478a-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0478a-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-700">Int64</span></span>|  
|<span data-ttu-id="0478a-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0478a-701">COLUMN_NAME</span></span>|<span data-ttu-id="0478a-702">String</span><span class="sxs-lookup"><span data-stu-id="0478a-702">String</span></span>|  
|<span data-ttu-id="0478a-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-703">COLUMN_GUID</span></span>|<span data-ttu-id="0478a-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0478a-704">Guid</span></span>|  
|<span data-ttu-id="0478a-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0478a-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0478a-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0478a-706">Int64</span></span>|  
|<span data-ttu-id="0478a-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0478a-707">COLLATION</span></span>|<span data-ttu-id="0478a-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0478a-708">Int16</span></span>|  
|<span data-ttu-id="0478a-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0478a-709">CARDINALITY</span></span>|<span data-ttu-id="0478a-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0478a-710">Decimal</span></span>|  
|<span data-ttu-id="0478a-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="0478a-711">PAGES</span></span>|<span data-ttu-id="0478a-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0478a-712">Int32</span></span>|  
|<span data-ttu-id="0478a-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0478a-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0478a-714">String</span><span class="sxs-lookup"><span data-stu-id="0478a-714">String</span></span>|  
|<span data-ttu-id="0478a-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0478a-715">INTEGRATED</span></span>|<span data-ttu-id="0478a-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="0478a-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0478a-717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0478a-717">See Also</span></span>  
 [<span data-ttu-id="0478a-718">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="0478a-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
