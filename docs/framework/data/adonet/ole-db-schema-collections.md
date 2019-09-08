---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783448"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="2c1df-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="2c1df-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="2c1df-103">W tej sekcji omówiono obsługę kolekcji schematów dla OLE DB dostawców dla Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="2c1df-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="2c1df-104">Dostawca OLE DB Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c1df-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="2c1df-105">Sterownik OLE DB Microsoft SQL Server obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="2c1df-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="2c1df-106">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-106">Tables</span></span>  
  
- <span data-ttu-id="2c1df-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-107">Columns</span></span>  
  
- <span data-ttu-id="2c1df-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-108">Procedures</span></span>  
  
- <span data-ttu-id="2c1df-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c1df-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="2c1df-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="2c1df-110">Catalog</span></span>  
  
- <span data-ttu-id="2c1df-111">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2c1df-112">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-112">Tables</span></span>  
  
|<span data-ttu-id="2c1df-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-113">ColumnName</span></span>|<span data-ttu-id="2c1df-114">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-115">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-116">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-116">String</span></span>|  
|<span data-ttu-id="2c1df-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-118">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-118">String</span></span>|  
|<span data-ttu-id="2c1df-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-119">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-120">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-120">String</span></span>|  
|<span data-ttu-id="2c1df-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-121">TABLE_TYPE</span></span>|<span data-ttu-id="2c1df-122">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-122">String</span></span>|  
|<span data-ttu-id="2c1df-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-123">TABLE_GUID</span></span>|<span data-ttu-id="2c1df-124">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-124">Guid</span></span>|  
|<span data-ttu-id="2c1df-125">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-125">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-126">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-126">String</span></span>|  
|<span data-ttu-id="2c1df-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-127">TABLE_PROPID</span></span>|<span data-ttu-id="2c1df-128">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-128">Int64</span></span>|  
|<span data-ttu-id="2c1df-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-129">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-130">DateTime</span></span>|  
|<span data-ttu-id="2c1df-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-131">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c1df-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-133">Columns</span></span>  
  
|<span data-ttu-id="2c1df-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-134">ColumnName</span></span>|<span data-ttu-id="2c1df-135">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-136">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-137">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-137">String</span></span>|  
|<span data-ttu-id="2c1df-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-139">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-139">String</span></span>|  
|<span data-ttu-id="2c1df-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-140">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-141">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-141">String</span></span>|  
|<span data-ttu-id="2c1df-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-142">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-143">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-143">String</span></span>|  
|<span data-ttu-id="2c1df-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-144">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-145">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-145">Guid</span></span>|  
|<span data-ttu-id="2c1df-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-146">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-147">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-147">Int64</span></span>|  
|<span data-ttu-id="2c1df-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-149">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-149">Int64</span></span>|  
|<span data-ttu-id="2c1df-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2c1df-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-151">Boolean</span></span>|  
|<span data-ttu-id="2c1df-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2c1df-153">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-153">String</span></span>|  
|<span data-ttu-id="2c1df-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2c1df-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="2c1df-155">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-155">Int64</span></span>|  
|<span data-ttu-id="2c1df-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-156">IS_NULLABLE</span></span>|<span data-ttu-id="2c1df-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-157">Boolean</span></span>|  
|<span data-ttu-id="2c1df-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-158">DATA_TYPE</span></span>|<span data-ttu-id="2c1df-159">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-159">Int32</span></span>|  
|<span data-ttu-id="2c1df-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-160">TYPE_GUID</span></span>|<span data-ttu-id="2c1df-161">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-161">Guid</span></span>|  
|<span data-ttu-id="2c1df-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2c1df-163">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-163">Int64</span></span>|  
|<span data-ttu-id="2c1df-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2c1df-165">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-165">Int64</span></span>|  
|<span data-ttu-id="2c1df-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2c1df-167">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-167">Int32</span></span>|  
|<span data-ttu-id="2c1df-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2c1df-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="2c1df-169">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-169">Int16</span></span>|  
|<span data-ttu-id="2c1df-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="2c1df-171">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-171">Int64</span></span>|  
|<span data-ttu-id="2c1df-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2c1df-173">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-173">String</span></span>|  
|<span data-ttu-id="2c1df-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2c1df-175">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-175">String</span></span>|  
|<span data-ttu-id="2c1df-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2c1df-177">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-177">String</span></span>|  
|<span data-ttu-id="2c1df-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="2c1df-179">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-179">String</span></span>|  
|<span data-ttu-id="2c1df-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2c1df-181">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-181">String</span></span>|  
|<span data-ttu-id="2c1df-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-182">COLLATION_NAME</span></span>|<span data-ttu-id="2c1df-183">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-183">String</span></span>|  
|<span data-ttu-id="2c1df-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2c1df-185">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-185">String</span></span>|  
|<span data-ttu-id="2c1df-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2c1df-187">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-187">String</span></span>|  
|<span data-ttu-id="2c1df-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-188">DOMAIN_NAME</span></span>|<span data-ttu-id="2c1df-189">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-189">String</span></span>|  
|<span data-ttu-id="2c1df-190">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-190">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-191">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-191">String</span></span>|  
|<span data-ttu-id="2c1df-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="2c1df-192">COLUMN_LCID</span></span>|<span data-ttu-id="2c1df-193">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-193">Int32</span></span>|  
|<span data-ttu-id="2c1df-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="2c1df-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="2c1df-195">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-195">Int32</span></span>|  
|<span data-ttu-id="2c1df-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="2c1df-196">COLUMN_SORTID</span></span>|<span data-ttu-id="2c1df-197">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-197">Int32</span></span>|  
|<span data-ttu-id="2c1df-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="2c1df-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="2c1df-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="2c1df-199">Byte[]</span></span>|  
|<span data-ttu-id="2c1df-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="2c1df-200">IS_COMPUTED</span></span>|<span data-ttu-id="2c1df-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c1df-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-202">Procedures</span></span>  
  
|<span data-ttu-id="2c1df-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-203">ColumnName</span></span>|<span data-ttu-id="2c1df-204">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2c1df-206">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-206">String</span></span>|  
|<span data-ttu-id="2c1df-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2c1df-208">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-208">String</span></span>|  
|<span data-ttu-id="2c1df-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c1df-210">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-210">String</span></span>|  
|<span data-ttu-id="2c1df-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c1df-212">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-212">Int16</span></span>|  
|<span data-ttu-id="2c1df-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2c1df-214">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-214">String</span></span>|  
|<span data-ttu-id="2c1df-215">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-215">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-216">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-216">String</span></span>|  
|<span data-ttu-id="2c1df-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-217">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-218">DateTime</span></span>|  
|<span data-ttu-id="2c1df-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-219">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2c1df-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c1df-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2c1df-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-222">ColumnName</span></span>|<span data-ttu-id="2c1df-223">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2c1df-225">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-225">String</span></span>|  
|<span data-ttu-id="2c1df-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2c1df-227">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-227">String</span></span>|  
|<span data-ttu-id="2c1df-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c1df-229">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-229">String</span></span>|  
|<span data-ttu-id="2c1df-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-230">PARAMETER_NAME</span></span>|<span data-ttu-id="2c1df-231">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-231">String</span></span>|  
|<span data-ttu-id="2c1df-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-233">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-233">Int32</span></span>|  
|<span data-ttu-id="2c1df-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="2c1df-235">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-235">Int32</span></span>|  
|<span data-ttu-id="2c1df-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="2c1df-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-237">Boolean</span></span>|  
|<span data-ttu-id="2c1df-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="2c1df-239">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-239">String</span></span>|  
|<span data-ttu-id="2c1df-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-240">IS_NULLABLE</span></span>|<span data-ttu-id="2c1df-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-241">Boolean</span></span>|  
|<span data-ttu-id="2c1df-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-242">DATA_TYPE</span></span>|<span data-ttu-id="2c1df-243">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-243">Int32</span></span>|  
|<span data-ttu-id="2c1df-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2c1df-245">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-245">Int64</span></span>|  
|<span data-ttu-id="2c1df-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2c1df-247">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-247">Int64</span></span>|  
|<span data-ttu-id="2c1df-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2c1df-249">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-249">Int32</span></span>|  
|<span data-ttu-id="2c1df-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2c1df-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="2c1df-251">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-251">Int16</span></span>|  
|<span data-ttu-id="2c1df-252">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-252">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-253">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-253">String</span></span>|  
|<span data-ttu-id="2c1df-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-254">TYPE_NAME</span></span>|<span data-ttu-id="2c1df-255">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-255">String</span></span>|  
|<span data-ttu-id="2c1df-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="2c1df-257">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="2c1df-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="2c1df-258">Catalog</span></span>  
  
|<span data-ttu-id="2c1df-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-259">ColumnName</span></span>|<span data-ttu-id="2c1df-260">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-261">CATALOG_NAME</span></span>|<span data-ttu-id="2c1df-262">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-262">String</span></span>|  
|<span data-ttu-id="2c1df-263">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-263">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-264">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2c1df-265">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-265">Indexes</span></span>  
  
|<span data-ttu-id="2c1df-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-266">ColumnName</span></span>|<span data-ttu-id="2c1df-267">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-268">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-269">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-269">String</span></span>|  
|<span data-ttu-id="2c1df-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-271">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-271">String</span></span>|  
|<span data-ttu-id="2c1df-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-272">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-273">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-273">String</span></span>|  
|<span data-ttu-id="2c1df-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-274">INDEX_CATALOG</span></span>|<span data-ttu-id="2c1df-275">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-275">String</span></span>|  
|<span data-ttu-id="2c1df-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="2c1df-277">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-277">String</span></span>|  
|<span data-ttu-id="2c1df-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-278">INDEX_NAME</span></span>|<span data-ttu-id="2c1df-279">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-279">String</span></span>|  
|<span data-ttu-id="2c1df-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2c1df-280">PRIMARY_KEY</span></span>|<span data-ttu-id="2c1df-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-281">Boolean</span></span>|  
|<span data-ttu-id="2c1df-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2c1df-282">UNIQUE</span></span>|<span data-ttu-id="2c1df-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-283">Boolean</span></span>|  
|<span data-ttu-id="2c1df-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2c1df-284">CLUSTERED</span></span>|<span data-ttu-id="2c1df-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-285">Boolean</span></span>|  
|<span data-ttu-id="2c1df-286">WPROWADŹ</span><span class="sxs-lookup"><span data-stu-id="2c1df-286">TYPE</span></span>|<span data-ttu-id="2c1df-287">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-287">Int32</span></span>|  
|<span data-ttu-id="2c1df-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2c1df-288">FILL_FACTOR</span></span>|<span data-ttu-id="2c1df-289">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-289">Int32</span></span>|  
|<span data-ttu-id="2c1df-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c1df-290">INITIAL_SIZE</span></span>|<span data-ttu-id="2c1df-291">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-291">Int32</span></span>|  
|<span data-ttu-id="2c1df-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2c1df-292">NULLS</span></span>|<span data-ttu-id="2c1df-293">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-293">Int32</span></span>|  
|<span data-ttu-id="2c1df-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2c1df-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2c1df-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-295">Boolean</span></span>|  
|<span data-ttu-id="2c1df-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2c1df-296">AUTO_UPDATE</span></span>|<span data-ttu-id="2c1df-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-297">Boolean</span></span>|  
|<span data-ttu-id="2c1df-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2c1df-298">NULL_COLLATION</span></span>|<span data-ttu-id="2c1df-299">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-299">Int32</span></span>|  
|<span data-ttu-id="2c1df-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-301">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-301">Int64</span></span>|  
|<span data-ttu-id="2c1df-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-302">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-303">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-303">String</span></span>|  
|<span data-ttu-id="2c1df-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-304">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-305">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-305">Guid</span></span>|  
|<span data-ttu-id="2c1df-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-306">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-307">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-307">Int64</span></span>|  
|<span data-ttu-id="2c1df-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2c1df-308">COLLATION</span></span>|<span data-ttu-id="2c1df-309">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-309">Int16</span></span>|  
|<span data-ttu-id="2c1df-310">KARDYNALNOŚCI</span><span class="sxs-lookup"><span data-stu-id="2c1df-310">CARDINALITY</span></span>|<span data-ttu-id="2c1df-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2c1df-311">Decimal</span></span>|  
|<span data-ttu-id="2c1df-312">PAGE</span><span class="sxs-lookup"><span data-stu-id="2c1df-312">PAGES</span></span>|<span data-ttu-id="2c1df-313">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-313">Int32</span></span>|  
|<span data-ttu-id="2c1df-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-314">FILTER_CONDITION</span></span>|<span data-ttu-id="2c1df-315">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-315">String</span></span>|  
|<span data-ttu-id="2c1df-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="2c1df-316">INTEGRATED</span></span>|<span data-ttu-id="2c1df-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="2c1df-318">Dostawca OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="2c1df-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="2c1df-319">Sterownik programu Microsoft Oracle OLE DB obsługuje następujące wybrane kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="2c1df-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="2c1df-320">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-320">Tables</span></span>  
  
- <span data-ttu-id="2c1df-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-321">Columns</span></span>  
  
- <span data-ttu-id="2c1df-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-322">Procedures</span></span>  
  
- <span data-ttu-id="2c1df-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c1df-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="2c1df-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2c1df-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="2c1df-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="2c1df-325">Views</span></span>  
  
- <span data-ttu-id="2c1df-326">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2c1df-327">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-327">Tables</span></span>  
  
|<span data-ttu-id="2c1df-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-328">ColumnName</span></span>|<span data-ttu-id="2c1df-329">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-330">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-331">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-331">String</span></span>|  
|<span data-ttu-id="2c1df-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-333">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-333">String</span></span>|  
|<span data-ttu-id="2c1df-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-334">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-335">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-335">String</span></span>|  
|<span data-ttu-id="2c1df-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-336">TABLE_TYPE</span></span>|<span data-ttu-id="2c1df-337">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-337">String</span></span>|  
|<span data-ttu-id="2c1df-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-338">TABLE_GUID</span></span>|<span data-ttu-id="2c1df-339">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-339">Guid</span></span>|  
|<span data-ttu-id="2c1df-340">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-340">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-341">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-341">String</span></span>|  
|<span data-ttu-id="2c1df-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-342">TABLE_PROPID</span></span>|<span data-ttu-id="2c1df-343">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-343">Int64</span></span>|  
|<span data-ttu-id="2c1df-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-344">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-345">DateTime</span></span>|  
|<span data-ttu-id="2c1df-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-346">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c1df-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-348">Columns</span></span>  
  
|<span data-ttu-id="2c1df-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-349">ColumnName</span></span>|<span data-ttu-id="2c1df-350">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-351">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-352">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-352">String</span></span>|  
|<span data-ttu-id="2c1df-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-354">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-354">String</span></span>|  
|<span data-ttu-id="2c1df-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-355">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-356">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-356">String</span></span>|  
|<span data-ttu-id="2c1df-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-357">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-358">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-358">String</span></span>|  
|<span data-ttu-id="2c1df-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-359">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-360">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-360">Guid</span></span>|  
|<span data-ttu-id="2c1df-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-361">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-362">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-362">Int64</span></span>|  
|<span data-ttu-id="2c1df-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-364">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-364">Int64</span></span>|  
|<span data-ttu-id="2c1df-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2c1df-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-366">Boolean</span></span>|  
|<span data-ttu-id="2c1df-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2c1df-368">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-368">String</span></span>|  
|<span data-ttu-id="2c1df-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2c1df-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="2c1df-370">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-370">Int64</span></span>|  
|<span data-ttu-id="2c1df-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-371">IS_NULLABLE</span></span>|<span data-ttu-id="2c1df-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-372">Boolean</span></span>|  
|<span data-ttu-id="2c1df-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-373">DATA_TYPE</span></span>|<span data-ttu-id="2c1df-374">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-374">Int32</span></span>|  
|<span data-ttu-id="2c1df-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-375">TYPE_GUID</span></span>|<span data-ttu-id="2c1df-376">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-376">Guid</span></span>|  
|<span data-ttu-id="2c1df-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2c1df-378">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-378">Int64</span></span>|  
|<span data-ttu-id="2c1df-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2c1df-380">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-380">Int64</span></span>|  
|<span data-ttu-id="2c1df-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2c1df-382">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-382">Int32</span></span>|  
|<span data-ttu-id="2c1df-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2c1df-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="2c1df-384">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-384">Int16</span></span>|  
|<span data-ttu-id="2c1df-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="2c1df-386">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-386">Int64</span></span>|  
|<span data-ttu-id="2c1df-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2c1df-388">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-388">String</span></span>|  
|<span data-ttu-id="2c1df-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2c1df-390">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-390">String</span></span>|  
|<span data-ttu-id="2c1df-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2c1df-392">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-392">String</span></span>|  
|<span data-ttu-id="2c1df-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="2c1df-394">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-394">String</span></span>|  
|<span data-ttu-id="2c1df-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2c1df-396">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-396">String</span></span>|  
|<span data-ttu-id="2c1df-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-397">COLLATION_NAME</span></span>|<span data-ttu-id="2c1df-398">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-398">String</span></span>|  
|<span data-ttu-id="2c1df-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2c1df-400">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-400">String</span></span>|  
|<span data-ttu-id="2c1df-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2c1df-402">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-402">String</span></span>|  
|<span data-ttu-id="2c1df-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-403">DOMAIN_NAME</span></span>|<span data-ttu-id="2c1df-404">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-404">String</span></span>|  
|<span data-ttu-id="2c1df-405">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-405">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-406">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c1df-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-407">Procedures</span></span>  
  
|<span data-ttu-id="2c1df-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-408">ColumnName</span></span>|<span data-ttu-id="2c1df-409">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2c1df-411">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-411">String</span></span>|  
|<span data-ttu-id="2c1df-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2c1df-413">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-413">String</span></span>|  
|<span data-ttu-id="2c1df-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c1df-415">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-415">String</span></span>|  
|<span data-ttu-id="2c1df-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c1df-417">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-417">Int16</span></span>|  
|<span data-ttu-id="2c1df-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2c1df-419">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-419">String</span></span>|  
|<span data-ttu-id="2c1df-420">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-420">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-421">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-421">String</span></span>|  
|<span data-ttu-id="2c1df-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-422">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-423">DateTime</span></span>|  
|<span data-ttu-id="2c1df-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-424">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2c1df-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2c1df-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2c1df-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-427">ColumnName</span></span>|<span data-ttu-id="2c1df-428">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2c1df-430">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-430">String</span></span>|  
|<span data-ttu-id="2c1df-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2c1df-432">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-432">String</span></span>|  
|<span data-ttu-id="2c1df-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c1df-434">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-434">String</span></span>|  
|<span data-ttu-id="2c1df-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-435">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-436">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-436">String</span></span>|  
|<span data-ttu-id="2c1df-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-437">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-438">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-438">Guid</span></span>|  
|<span data-ttu-id="2c1df-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-439">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-440">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-440">Int64</span></span>|  
|<span data-ttu-id="2c1df-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="2c1df-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="2c1df-442">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-442">Int64</span></span>|  
|<span data-ttu-id="2c1df-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-444">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-444">Int64</span></span>|  
|<span data-ttu-id="2c1df-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-445">IS_NULLABLE</span></span>|<span data-ttu-id="2c1df-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-446">Boolean</span></span>|  
|<span data-ttu-id="2c1df-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-447">DATA_TYPE</span></span>|<span data-ttu-id="2c1df-448">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-448">Int32</span></span>|  
|<span data-ttu-id="2c1df-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-449">TYPE_GUID</span></span>|<span data-ttu-id="2c1df-450">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-450">Guid</span></span>|  
|<span data-ttu-id="2c1df-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2c1df-452">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-452">Int64</span></span>|  
|<span data-ttu-id="2c1df-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2c1df-454">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-454">Int64</span></span>|  
|<span data-ttu-id="2c1df-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2c1df-456">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-456">Int32</span></span>|  
|<span data-ttu-id="2c1df-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2c1df-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="2c1df-458">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-458">Int16</span></span>|  
|<span data-ttu-id="2c1df-459">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-459">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-460">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-460">String</span></span>|  
|<span data-ttu-id="2c1df-461">WYSTĘPUJĄ</span><span class="sxs-lookup"><span data-stu-id="2c1df-461">OVERLOAD</span></span>|<span data-ttu-id="2c1df-462">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="2c1df-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="2c1df-463">Views</span></span>  
  
|<span data-ttu-id="2c1df-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-464">ColumnName</span></span>|<span data-ttu-id="2c1df-465">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-466">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-467">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-467">String</span></span>|  
|<span data-ttu-id="2c1df-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-469">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-469">String</span></span>|  
|<span data-ttu-id="2c1df-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-470">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-471">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-471">String</span></span>|  
|<span data-ttu-id="2c1df-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="2c1df-473">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-473">String</span></span>|  
|<span data-ttu-id="2c1df-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="2c1df-474">CHECK_OPTION</span></span>|<span data-ttu-id="2c1df-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-475">Boolean</span></span>|  
|<span data-ttu-id="2c1df-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-476">IS_UPDATABLE</span></span>|<span data-ttu-id="2c1df-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-477">Boolean</span></span>|  
|<span data-ttu-id="2c1df-478">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-478">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-479">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-479">String</span></span>|  
|<span data-ttu-id="2c1df-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-480">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-481">DateTime</span></span>|  
|<span data-ttu-id="2c1df-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-482">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2c1df-484">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-484">Indexes</span></span>  
  
|<span data-ttu-id="2c1df-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-485">ColumnName</span></span>|<span data-ttu-id="2c1df-486">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-487">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-488">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-488">String</span></span>|  
|<span data-ttu-id="2c1df-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-490">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-490">String</span></span>|  
|<span data-ttu-id="2c1df-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-491">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-492">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-492">String</span></span>|  
|<span data-ttu-id="2c1df-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-493">INDEX_CATALOG</span></span>|<span data-ttu-id="2c1df-494">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-494">String</span></span>|  
|<span data-ttu-id="2c1df-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="2c1df-496">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-496">String</span></span>|  
|<span data-ttu-id="2c1df-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-497">INDEX_NAME</span></span>|<span data-ttu-id="2c1df-498">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-498">String</span></span>|  
|<span data-ttu-id="2c1df-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2c1df-499">PRIMARY_KEY</span></span>|<span data-ttu-id="2c1df-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-500">Boolean</span></span>|  
|<span data-ttu-id="2c1df-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2c1df-501">UNIQUE</span></span>|<span data-ttu-id="2c1df-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-502">Boolean</span></span>|  
|<span data-ttu-id="2c1df-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2c1df-503">CLUSTERED</span></span>|<span data-ttu-id="2c1df-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-504">Boolean</span></span>|  
|<span data-ttu-id="2c1df-505">WPROWADŹ</span><span class="sxs-lookup"><span data-stu-id="2c1df-505">TYPE</span></span>|<span data-ttu-id="2c1df-506">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-506">Int32</span></span>|  
|<span data-ttu-id="2c1df-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2c1df-507">FILL_FACTOR</span></span>|<span data-ttu-id="2c1df-508">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-508">Int32</span></span>|  
|<span data-ttu-id="2c1df-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c1df-509">INITIAL_SIZE</span></span>|<span data-ttu-id="2c1df-510">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-510">Int32</span></span>|  
|<span data-ttu-id="2c1df-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2c1df-511">NULLS</span></span>|<span data-ttu-id="2c1df-512">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-512">Int32</span></span>|  
|<span data-ttu-id="2c1df-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2c1df-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2c1df-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-514">Boolean</span></span>|  
|<span data-ttu-id="2c1df-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2c1df-515">AUTO_UPDATE</span></span>|<span data-ttu-id="2c1df-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-516">Boolean</span></span>|  
|<span data-ttu-id="2c1df-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2c1df-517">NULL_COLLATION</span></span>|<span data-ttu-id="2c1df-518">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-518">Int32</span></span>|  
|<span data-ttu-id="2c1df-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-520">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-520">Int64</span></span>|  
|<span data-ttu-id="2c1df-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-521">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-522">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-522">String</span></span>|  
|<span data-ttu-id="2c1df-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-523">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-524">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-524">Guid</span></span>|  
|<span data-ttu-id="2c1df-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-525">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-526">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-526">Int64</span></span>|  
|<span data-ttu-id="2c1df-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2c1df-527">COLLATION</span></span>|<span data-ttu-id="2c1df-528">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-528">Int16</span></span>|  
|<span data-ttu-id="2c1df-529">KARDYNALNOŚCI</span><span class="sxs-lookup"><span data-stu-id="2c1df-529">CARDINALITY</span></span>|<span data-ttu-id="2c1df-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2c1df-530">Decimal</span></span>|  
|<span data-ttu-id="2c1df-531">PAGE</span><span class="sxs-lookup"><span data-stu-id="2c1df-531">PAGES</span></span>|<span data-ttu-id="2c1df-532">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-532">Int32</span></span>|  
|<span data-ttu-id="2c1df-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-533">FILTER_CONDITION</span></span>|<span data-ttu-id="2c1df-534">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-534">String</span></span>|  
|<span data-ttu-id="2c1df-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="2c1df-535">INTEGRATED</span></span>|<span data-ttu-id="2c1df-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="2c1df-537">Dostawca OLE DB Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="2c1df-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="2c1df-538">Sterownik programu Microsoft Jet OLE DB obsługuje następujące kolekcje schematów oprócz wspólnych kolekcji schematów:</span><span class="sxs-lookup"><span data-stu-id="2c1df-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="2c1df-539">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-539">Tables</span></span>  
  
- <span data-ttu-id="2c1df-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-540">Columns</span></span>  
  
- <span data-ttu-id="2c1df-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-541">Procedures</span></span>  
  
- <span data-ttu-id="2c1df-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="2c1df-542">Views</span></span>  
  
- <span data-ttu-id="2c1df-543">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2c1df-544">Tabelę</span><span class="sxs-lookup"><span data-stu-id="2c1df-544">Tables</span></span>  
  
|<span data-ttu-id="2c1df-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-545">ColumnName</span></span>|<span data-ttu-id="2c1df-546">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-547">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-548">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-548">String</span></span>|  
|<span data-ttu-id="2c1df-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-550">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-550">String</span></span>|  
|<span data-ttu-id="2c1df-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-551">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-552">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-552">String</span></span>|  
|<span data-ttu-id="2c1df-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-553">TABLE_TYPE</span></span>|<span data-ttu-id="2c1df-554">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-554">String</span></span>|  
|<span data-ttu-id="2c1df-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-555">TABLE_GUID</span></span>|<span data-ttu-id="2c1df-556">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-556">Guid</span></span>|  
|<span data-ttu-id="2c1df-557">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-557">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-558">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-558">String</span></span>|  
|<span data-ttu-id="2c1df-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-559">TABLE_PROPID</span></span>|<span data-ttu-id="2c1df-560">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-560">Int64</span></span>|  
|<span data-ttu-id="2c1df-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-561">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-562">DateTime</span></span>|  
|<span data-ttu-id="2c1df-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-563">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2c1df-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2c1df-565">Columns</span></span>  
  
|<span data-ttu-id="2c1df-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-566">ColumnName</span></span>|<span data-ttu-id="2c1df-567">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-568">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-569">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-569">String</span></span>|  
|<span data-ttu-id="2c1df-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-571">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-571">String</span></span>|  
|<span data-ttu-id="2c1df-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-572">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-573">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-573">String</span></span>|  
|<span data-ttu-id="2c1df-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-574">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-575">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-575">String</span></span>|  
|<span data-ttu-id="2c1df-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-576">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-577">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-577">Guid</span></span>|  
|<span data-ttu-id="2c1df-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-578">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-579">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-579">Int64</span></span>|  
|<span data-ttu-id="2c1df-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-581">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-581">Int64</span></span>|  
|<span data-ttu-id="2c1df-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2c1df-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-583">Boolean</span></span>|  
|<span data-ttu-id="2c1df-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2c1df-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2c1df-585">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-585">String</span></span>|  
|<span data-ttu-id="2c1df-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2c1df-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="2c1df-587">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-587">Int64</span></span>|  
|<span data-ttu-id="2c1df-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-588">IS_NULLABLE</span></span>|<span data-ttu-id="2c1df-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-589">Boolean</span></span>|  
|<span data-ttu-id="2c1df-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-590">DATA_TYPE</span></span>|<span data-ttu-id="2c1df-591">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-591">Int32</span></span>|  
|<span data-ttu-id="2c1df-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-592">TYPE_GUID</span></span>|<span data-ttu-id="2c1df-593">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-593">Guid</span></span>|  
|<span data-ttu-id="2c1df-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2c1df-595">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-595">Int64</span></span>|  
|<span data-ttu-id="2c1df-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2c1df-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2c1df-597">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-597">Int64</span></span>|  
|<span data-ttu-id="2c1df-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2c1df-599">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-599">Int32</span></span>|  
|<span data-ttu-id="2c1df-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2c1df-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="2c1df-601">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-601">Int16</span></span>|  
|<span data-ttu-id="2c1df-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2c1df-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="2c1df-603">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-603">Int64</span></span>|  
|<span data-ttu-id="2c1df-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2c1df-605">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-605">String</span></span>|  
|<span data-ttu-id="2c1df-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2c1df-607">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-607">String</span></span>|  
|<span data-ttu-id="2c1df-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2c1df-609">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-609">String</span></span>|  
|<span data-ttu-id="2c1df-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="2c1df-611">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-611">String</span></span>|  
|<span data-ttu-id="2c1df-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2c1df-613">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-613">String</span></span>|  
|<span data-ttu-id="2c1df-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-614">COLLATION_NAME</span></span>|<span data-ttu-id="2c1df-615">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-615">String</span></span>|  
|<span data-ttu-id="2c1df-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2c1df-617">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-617">String</span></span>|  
|<span data-ttu-id="2c1df-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2c1df-619">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-619">String</span></span>|  
|<span data-ttu-id="2c1df-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-620">DOMAIN_NAME</span></span>|<span data-ttu-id="2c1df-621">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-621">String</span></span>|  
|<span data-ttu-id="2c1df-622">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-622">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-623">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2c1df-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c1df-624">Procedures</span></span>  
  
|<span data-ttu-id="2c1df-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-625">ColumnName</span></span>|<span data-ttu-id="2c1df-626">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2c1df-628">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-628">String</span></span>|  
|<span data-ttu-id="2c1df-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2c1df-630">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-630">String</span></span>|  
|<span data-ttu-id="2c1df-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="2c1df-632">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-632">String</span></span>|  
|<span data-ttu-id="2c1df-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2c1df-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2c1df-634">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-634">Int16</span></span>|  
|<span data-ttu-id="2c1df-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2c1df-636">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-636">String</span></span>|  
|<span data-ttu-id="2c1df-637">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-637">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-638">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-638">String</span></span>|  
|<span data-ttu-id="2c1df-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-639">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-640">DateTime</span></span>|  
|<span data-ttu-id="2c1df-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-641">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="2c1df-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="2c1df-643">Views</span></span>  
  
|<span data-ttu-id="2c1df-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-644">ColumnName</span></span>|<span data-ttu-id="2c1df-645">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-646">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-647">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-647">String</span></span>|  
|<span data-ttu-id="2c1df-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-649">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-649">String</span></span>|  
|<span data-ttu-id="2c1df-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-650">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-651">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-651">String</span></span>|  
|<span data-ttu-id="2c1df-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="2c1df-653">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-653">String</span></span>|  
|<span data-ttu-id="2c1df-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="2c1df-654">CHECK_OPTION</span></span>|<span data-ttu-id="2c1df-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-655">Boolean</span></span>|  
|<span data-ttu-id="2c1df-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="2c1df-656">IS_UPDATABLE</span></span>|<span data-ttu-id="2c1df-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-657">Boolean</span></span>|  
|<span data-ttu-id="2c1df-658">ZHARMONIZOWAN</span><span class="sxs-lookup"><span data-stu-id="2c1df-658">DESCRIPTION</span></span>|<span data-ttu-id="2c1df-659">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-659">String</span></span>|  
|<span data-ttu-id="2c1df-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2c1df-660">DATE_CREATED</span></span>|<span data-ttu-id="2c1df-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-661">DateTime</span></span>|  
|<span data-ttu-id="2c1df-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2c1df-662">DATE_MODIFIED</span></span>|<span data-ttu-id="2c1df-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2c1df-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2c1df-664">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="2c1df-664">Indexes</span></span>  
  
|<span data-ttu-id="2c1df-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="2c1df-665">ColumnName</span></span>|<span data-ttu-id="2c1df-666">DataType</span><span class="sxs-lookup"><span data-stu-id="2c1df-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2c1df-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-667">TABLE_CATALOG</span></span>|<span data-ttu-id="2c1df-668">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-668">String</span></span>|  
|<span data-ttu-id="2c1df-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="2c1df-670">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-670">String</span></span>|  
|<span data-ttu-id="2c1df-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-671">TABLE_NAME</span></span>|<span data-ttu-id="2c1df-672">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-672">String</span></span>|  
|<span data-ttu-id="2c1df-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2c1df-673">INDEX_CATALOG</span></span>|<span data-ttu-id="2c1df-674">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-674">String</span></span>|  
|<span data-ttu-id="2c1df-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2c1df-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="2c1df-676">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-676">String</span></span>|  
|<span data-ttu-id="2c1df-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-677">INDEX_NAME</span></span>|<span data-ttu-id="2c1df-678">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-678">String</span></span>|  
|<span data-ttu-id="2c1df-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2c1df-679">PRIMARY_KEY</span></span>|<span data-ttu-id="2c1df-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-680">Boolean</span></span>|  
|<span data-ttu-id="2c1df-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2c1df-681">UNIQUE</span></span>|<span data-ttu-id="2c1df-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-682">Boolean</span></span>|  
|<span data-ttu-id="2c1df-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2c1df-683">CLUSTERED</span></span>|<span data-ttu-id="2c1df-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-684">Boolean</span></span>|  
|<span data-ttu-id="2c1df-685">WPROWADŹ</span><span class="sxs-lookup"><span data-stu-id="2c1df-685">TYPE</span></span>|<span data-ttu-id="2c1df-686">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-686">Int32</span></span>|  
|<span data-ttu-id="2c1df-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2c1df-687">FILL_FACTOR</span></span>|<span data-ttu-id="2c1df-688">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-688">Int32</span></span>|  
|<span data-ttu-id="2c1df-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2c1df-689">INITIAL_SIZE</span></span>|<span data-ttu-id="2c1df-690">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-690">Int32</span></span>|  
|<span data-ttu-id="2c1df-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2c1df-691">NULLS</span></span>|<span data-ttu-id="2c1df-692">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-692">Int32</span></span>|  
|<span data-ttu-id="2c1df-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2c1df-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2c1df-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-694">Boolean</span></span>|  
|<span data-ttu-id="2c1df-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2c1df-695">AUTO_UPDATE</span></span>|<span data-ttu-id="2c1df-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-696">Boolean</span></span>|  
|<span data-ttu-id="2c1df-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2c1df-697">NULL_COLLATION</span></span>|<span data-ttu-id="2c1df-698">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-698">Int32</span></span>|  
|<span data-ttu-id="2c1df-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="2c1df-700">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-700">Int64</span></span>|  
|<span data-ttu-id="2c1df-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2c1df-701">COLUMN_NAME</span></span>|<span data-ttu-id="2c1df-702">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-702">String</span></span>|  
|<span data-ttu-id="2c1df-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2c1df-703">COLUMN_GUID</span></span>|<span data-ttu-id="2c1df-704">Guid</span><span class="sxs-lookup"><span data-stu-id="2c1df-704">Guid</span></span>|  
|<span data-ttu-id="2c1df-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2c1df-705">COLUMN_PROPID</span></span>|<span data-ttu-id="2c1df-706">Int64</span><span class="sxs-lookup"><span data-stu-id="2c1df-706">Int64</span></span>|  
|<span data-ttu-id="2c1df-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2c1df-707">COLLATION</span></span>|<span data-ttu-id="2c1df-708">Int16</span><span class="sxs-lookup"><span data-stu-id="2c1df-708">Int16</span></span>|  
|<span data-ttu-id="2c1df-709">KARDYNALNOŚCI</span><span class="sxs-lookup"><span data-stu-id="2c1df-709">CARDINALITY</span></span>|<span data-ttu-id="2c1df-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2c1df-710">Decimal</span></span>|  
|<span data-ttu-id="2c1df-711">PAGE</span><span class="sxs-lookup"><span data-stu-id="2c1df-711">PAGES</span></span>|<span data-ttu-id="2c1df-712">Int32</span><span class="sxs-lookup"><span data-stu-id="2c1df-712">Int32</span></span>|  
|<span data-ttu-id="2c1df-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2c1df-713">FILTER_CONDITION</span></span>|<span data-ttu-id="2c1df-714">String</span><span class="sxs-lookup"><span data-stu-id="2c1df-714">String</span></span>|  
|<span data-ttu-id="2c1df-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="2c1df-715">INTEGRATED</span></span>|<span data-ttu-id="2c1df-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="2c1df-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c1df-717">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c1df-717">See also</span></span>

- [<span data-ttu-id="2c1df-718">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2c1df-718">ADO.NET Overview</span></span>](ado-net-overview.md)
