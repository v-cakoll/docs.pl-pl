---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164687"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="bcbfc-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="bcbfc-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="bcbfc-103">W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="bcbfc-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="bcbfc-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="bcbfc-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="bcbfc-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="bcbfc-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="bcbfc-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-106">Tables</span></span>  
  
-   <span data-ttu-id="bcbfc-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-107">Columns</span></span>  
  
-   <span data-ttu-id="bcbfc-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-108">Procedures</span></span>  
  
-   <span data-ttu-id="bcbfc-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="bcbfc-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="bcbfc-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="bcbfc-110">Catalog</span></span>  
  
-   <span data-ttu-id="bcbfc-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="bcbfc-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-112">Tables</span></span>  
  
|<span data-ttu-id="bcbfc-113">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-113">ColumnName</span></span>|<span data-ttu-id="bcbfc-114">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-115">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-116">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-116">String</span></span>|  
|<span data-ttu-id="bcbfc-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-118">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-118">String</span></span>|  
|<span data-ttu-id="bcbfc-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-119">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-120">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-120">String</span></span>|  
|<span data-ttu-id="bcbfc-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-121">TABLE_TYPE</span></span>|<span data-ttu-id="bcbfc-122">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-122">String</span></span>|  
|<span data-ttu-id="bcbfc-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-123">TABLE_GUID</span></span>|<span data-ttu-id="bcbfc-124">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-124">Guid</span></span>|  
|<span data-ttu-id="bcbfc-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-125">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-126">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-126">String</span></span>|  
|<span data-ttu-id="bcbfc-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-127">TABLE_PROPID</span></span>|<span data-ttu-id="bcbfc-128">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-128">Int64</span></span>|  
|<span data-ttu-id="bcbfc-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-129">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-130">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-131">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="bcbfc-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-133">Columns</span></span>  
  
|<span data-ttu-id="bcbfc-134">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-134">ColumnName</span></span>|<span data-ttu-id="bcbfc-135">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-136">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-137">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-137">String</span></span>|  
|<span data-ttu-id="bcbfc-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-139">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-139">String</span></span>|  
|<span data-ttu-id="bcbfc-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-140">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-141">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-141">String</span></span>|  
|<span data-ttu-id="bcbfc-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-142">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-143">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-143">String</span></span>|  
|<span data-ttu-id="bcbfc-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-144">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-145">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-145">Guid</span></span>|  
|<span data-ttu-id="bcbfc-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-146">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-147">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-147">Int64</span></span>|  
|<span data-ttu-id="bcbfc-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-149">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-149">Int64</span></span>|  
|<span data-ttu-id="bcbfc-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="bcbfc-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-151">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="bcbfc-153">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-153">String</span></span>|  
|<span data-ttu-id="bcbfc-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="bcbfc-155">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-155">Int64</span></span>|  
|<span data-ttu-id="bcbfc-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-156">IS_NULLABLE</span></span>|<span data-ttu-id="bcbfc-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-157">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-158">DATA_TYPE</span></span>|<span data-ttu-id="bcbfc-159">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-159">Int32</span></span>|  
|<span data-ttu-id="bcbfc-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-160">TYPE_GUID</span></span>|<span data-ttu-id="bcbfc-161">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-161">Guid</span></span>|  
|<span data-ttu-id="bcbfc-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="bcbfc-163">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-163">Int64</span></span>|  
|<span data-ttu-id="bcbfc-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="bcbfc-165">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-165">Int64</span></span>|  
|<span data-ttu-id="bcbfc-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="bcbfc-167">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-167">Int32</span></span>|  
|<span data-ttu-id="bcbfc-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="bcbfc-169">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-169">Int16</span></span>|  
|<span data-ttu-id="bcbfc-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="bcbfc-171">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-171">Int64</span></span>|  
|<span data-ttu-id="bcbfc-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="bcbfc-173">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-173">String</span></span>|  
|<span data-ttu-id="bcbfc-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="bcbfc-175">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-175">String</span></span>|  
|<span data-ttu-id="bcbfc-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="bcbfc-177">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-177">String</span></span>|  
|<span data-ttu-id="bcbfc-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="bcbfc-179">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-179">String</span></span>|  
|<span data-ttu-id="bcbfc-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="bcbfc-181">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-181">String</span></span>|  
|<span data-ttu-id="bcbfc-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-182">COLLATION_NAME</span></span>|<span data-ttu-id="bcbfc-183">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-183">String</span></span>|  
|<span data-ttu-id="bcbfc-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="bcbfc-185">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-185">String</span></span>|  
|<span data-ttu-id="bcbfc-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="bcbfc-187">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-187">String</span></span>|  
|<span data-ttu-id="bcbfc-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-188">DOMAIN_NAME</span></span>|<span data-ttu-id="bcbfc-189">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-189">String</span></span>|  
|<span data-ttu-id="bcbfc-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-190">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-191">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-191">String</span></span>|  
|<span data-ttu-id="bcbfc-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-192">COLUMN_LCID</span></span>|<span data-ttu-id="bcbfc-193">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-193">Int32</span></span>|  
|<span data-ttu-id="bcbfc-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="bcbfc-195">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-195">Int32</span></span>|  
|<span data-ttu-id="bcbfc-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-196">COLUMN_SORTID</span></span>|<span data-ttu-id="bcbfc-197">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-197">Int32</span></span>|  
|<span data-ttu-id="bcbfc-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="bcbfc-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="bcbfc-199">Byte[]</span></span>|  
|<span data-ttu-id="bcbfc-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-200">IS_COMPUTED</span></span>|<span data-ttu-id="bcbfc-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="bcbfc-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-202">Procedures</span></span>  
  
|<span data-ttu-id="bcbfc-203">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-203">ColumnName</span></span>|<span data-ttu-id="bcbfc-204">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="bcbfc-206">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-206">String</span></span>|  
|<span data-ttu-id="bcbfc-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-208">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-208">String</span></span>|  
|<span data-ttu-id="bcbfc-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="bcbfc-210">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-210">String</span></span>|  
|<span data-ttu-id="bcbfc-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="bcbfc-212">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-212">Int16</span></span>|  
|<span data-ttu-id="bcbfc-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="bcbfc-214">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-214">String</span></span>|  
|<span data-ttu-id="bcbfc-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-215">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-216">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-216">String</span></span>|  
|<span data-ttu-id="bcbfc-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-217">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-218">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-219">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="bcbfc-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="bcbfc-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="bcbfc-222">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-222">ColumnName</span></span>|<span data-ttu-id="bcbfc-223">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="bcbfc-225">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-225">String</span></span>|  
|<span data-ttu-id="bcbfc-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-227">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-227">String</span></span>|  
|<span data-ttu-id="bcbfc-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="bcbfc-229">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-229">String</span></span>|  
|<span data-ttu-id="bcbfc-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-230">PARAMETER_NAME</span></span>|<span data-ttu-id="bcbfc-231">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-231">String</span></span>|  
|<span data-ttu-id="bcbfc-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-233">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-233">Int32</span></span>|  
|<span data-ttu-id="bcbfc-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="bcbfc-235">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-235">Int32</span></span>|  
|<span data-ttu-id="bcbfc-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="bcbfc-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-237">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="bcbfc-239">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-239">String</span></span>|  
|<span data-ttu-id="bcbfc-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-240">IS_NULLABLE</span></span>|<span data-ttu-id="bcbfc-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-241">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-242">DATA_TYPE</span></span>|<span data-ttu-id="bcbfc-243">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-243">Int32</span></span>|  
|<span data-ttu-id="bcbfc-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="bcbfc-245">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-245">Int64</span></span>|  
|<span data-ttu-id="bcbfc-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="bcbfc-247">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-247">Int64</span></span>|  
|<span data-ttu-id="bcbfc-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="bcbfc-249">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-249">Int32</span></span>|  
|<span data-ttu-id="bcbfc-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="bcbfc-251">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-251">Int16</span></span>|  
|<span data-ttu-id="bcbfc-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-252">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-253">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-253">String</span></span>|  
|<span data-ttu-id="bcbfc-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-254">TYPE_NAME</span></span>|<span data-ttu-id="bcbfc-255">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-255">String</span></span>|  
|<span data-ttu-id="bcbfc-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="bcbfc-257">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="bcbfc-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="bcbfc-258">Catalog</span></span>  
  
|<span data-ttu-id="bcbfc-259">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-259">ColumnName</span></span>|<span data-ttu-id="bcbfc-260">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-261">CATALOG_NAME</span></span>|<span data-ttu-id="bcbfc-262">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-262">String</span></span>|  
|<span data-ttu-id="bcbfc-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-263">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-264">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="bcbfc-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-265">Indexes</span></span>  
  
|<span data-ttu-id="bcbfc-266">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-266">ColumnName</span></span>|<span data-ttu-id="bcbfc-267">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-268">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-269">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-269">String</span></span>|  
|<span data-ttu-id="bcbfc-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-271">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-271">String</span></span>|  
|<span data-ttu-id="bcbfc-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-272">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-273">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-273">String</span></span>|  
|<span data-ttu-id="bcbfc-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-274">INDEX_CATALOG</span></span>|<span data-ttu-id="bcbfc-275">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-275">String</span></span>|  
|<span data-ttu-id="bcbfc-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="bcbfc-277">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-277">String</span></span>|  
|<span data-ttu-id="bcbfc-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-278">INDEX_NAME</span></span>|<span data-ttu-id="bcbfc-279">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-279">String</span></span>|  
|<span data-ttu-id="bcbfc-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-280">PRIMARY_KEY</span></span>|<span data-ttu-id="bcbfc-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-281">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-282">UNIQUE</span></span>|<span data-ttu-id="bcbfc-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-283">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-284">CLUSTERED</span></span>|<span data-ttu-id="bcbfc-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-285">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-286">TYP</span><span class="sxs-lookup"><span data-stu-id="bcbfc-286">TYPE</span></span>|<span data-ttu-id="bcbfc-287">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-287">Int32</span></span>|  
|<span data-ttu-id="bcbfc-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="bcbfc-288">FILL_FACTOR</span></span>|<span data-ttu-id="bcbfc-289">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-289">Int32</span></span>|  
|<span data-ttu-id="bcbfc-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-290">INITIAL_SIZE</span></span>|<span data-ttu-id="bcbfc-291">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-291">Int32</span></span>|  
|<span data-ttu-id="bcbfc-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="bcbfc-292">NULLS</span></span>|<span data-ttu-id="bcbfc-293">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-293">Int32</span></span>|  
|<span data-ttu-id="bcbfc-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="bcbfc-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-295">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-296">AUTO_UPDATE</span></span>|<span data-ttu-id="bcbfc-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-297">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-298">NULL_COLLATION</span></span>|<span data-ttu-id="bcbfc-299">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-299">Int32</span></span>|  
|<span data-ttu-id="bcbfc-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-301">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-301">Int64</span></span>|  
|<span data-ttu-id="bcbfc-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-302">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-303">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-303">String</span></span>|  
|<span data-ttu-id="bcbfc-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-304">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-305">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-305">Guid</span></span>|  
|<span data-ttu-id="bcbfc-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-306">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-307">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-307">Int64</span></span>|  
|<span data-ttu-id="bcbfc-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-308">COLLATION</span></span>|<span data-ttu-id="bcbfc-309">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-309">Int16</span></span>|  
|<span data-ttu-id="bcbfc-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="bcbfc-310">CARDINALITY</span></span>|<span data-ttu-id="bcbfc-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="bcbfc-311">Decimal</span></span>|  
|<span data-ttu-id="bcbfc-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-312">PAGES</span></span>|<span data-ttu-id="bcbfc-313">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-313">Int32</span></span>|  
|<span data-ttu-id="bcbfc-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-314">FILTER_CONDITION</span></span>|<span data-ttu-id="bcbfc-315">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-315">String</span></span>|  
|<span data-ttu-id="bcbfc-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-316">INTEGRATED</span></span>|<span data-ttu-id="bcbfc-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="bcbfc-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="bcbfc-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="bcbfc-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="bcbfc-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="bcbfc-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-320">Tables</span></span>  
  
-   <span data-ttu-id="bcbfc-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-321">Columns</span></span>  
  
-   <span data-ttu-id="bcbfc-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-322">Procedures</span></span>  
  
-   <span data-ttu-id="bcbfc-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="bcbfc-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="bcbfc-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="bcbfc-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="bcbfc-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="bcbfc-325">Views</span></span>  
  
-   <span data-ttu-id="bcbfc-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="bcbfc-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-327">Tables</span></span>  
  
|<span data-ttu-id="bcbfc-328">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-328">ColumnName</span></span>|<span data-ttu-id="bcbfc-329">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-330">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-331">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-331">String</span></span>|  
|<span data-ttu-id="bcbfc-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-333">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-333">String</span></span>|  
|<span data-ttu-id="bcbfc-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-334">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-335">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-335">String</span></span>|  
|<span data-ttu-id="bcbfc-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-336">TABLE_TYPE</span></span>|<span data-ttu-id="bcbfc-337">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-337">String</span></span>|  
|<span data-ttu-id="bcbfc-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-338">TABLE_GUID</span></span>|<span data-ttu-id="bcbfc-339">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-339">Guid</span></span>|  
|<span data-ttu-id="bcbfc-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-340">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-341">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-341">String</span></span>|  
|<span data-ttu-id="bcbfc-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-342">TABLE_PROPID</span></span>|<span data-ttu-id="bcbfc-343">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-343">Int64</span></span>|  
|<span data-ttu-id="bcbfc-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-344">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-345">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-346">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="bcbfc-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-348">Columns</span></span>  
  
|<span data-ttu-id="bcbfc-349">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-349">ColumnName</span></span>|<span data-ttu-id="bcbfc-350">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-351">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-352">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-352">String</span></span>|  
|<span data-ttu-id="bcbfc-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-354">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-354">String</span></span>|  
|<span data-ttu-id="bcbfc-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-355">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-356">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-356">String</span></span>|  
|<span data-ttu-id="bcbfc-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-357">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-358">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-358">String</span></span>|  
|<span data-ttu-id="bcbfc-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-359">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-360">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-360">Guid</span></span>|  
|<span data-ttu-id="bcbfc-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-361">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-362">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-362">Int64</span></span>|  
|<span data-ttu-id="bcbfc-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-364">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-364">Int64</span></span>|  
|<span data-ttu-id="bcbfc-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="bcbfc-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-366">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="bcbfc-368">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-368">String</span></span>|  
|<span data-ttu-id="bcbfc-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="bcbfc-370">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-370">Int64</span></span>|  
|<span data-ttu-id="bcbfc-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-371">IS_NULLABLE</span></span>|<span data-ttu-id="bcbfc-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-372">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-373">DATA_TYPE</span></span>|<span data-ttu-id="bcbfc-374">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-374">Int32</span></span>|  
|<span data-ttu-id="bcbfc-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-375">TYPE_GUID</span></span>|<span data-ttu-id="bcbfc-376">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-376">Guid</span></span>|  
|<span data-ttu-id="bcbfc-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="bcbfc-378">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-378">Int64</span></span>|  
|<span data-ttu-id="bcbfc-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="bcbfc-380">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-380">Int64</span></span>|  
|<span data-ttu-id="bcbfc-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="bcbfc-382">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-382">Int32</span></span>|  
|<span data-ttu-id="bcbfc-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="bcbfc-384">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-384">Int16</span></span>|  
|<span data-ttu-id="bcbfc-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="bcbfc-386">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-386">Int64</span></span>|  
|<span data-ttu-id="bcbfc-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="bcbfc-388">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-388">String</span></span>|  
|<span data-ttu-id="bcbfc-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="bcbfc-390">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-390">String</span></span>|  
|<span data-ttu-id="bcbfc-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="bcbfc-392">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-392">String</span></span>|  
|<span data-ttu-id="bcbfc-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="bcbfc-394">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-394">String</span></span>|  
|<span data-ttu-id="bcbfc-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="bcbfc-396">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-396">String</span></span>|  
|<span data-ttu-id="bcbfc-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-397">COLLATION_NAME</span></span>|<span data-ttu-id="bcbfc-398">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-398">String</span></span>|  
|<span data-ttu-id="bcbfc-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="bcbfc-400">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-400">String</span></span>|  
|<span data-ttu-id="bcbfc-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="bcbfc-402">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-402">String</span></span>|  
|<span data-ttu-id="bcbfc-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-403">DOMAIN_NAME</span></span>|<span data-ttu-id="bcbfc-404">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-404">String</span></span>|  
|<span data-ttu-id="bcbfc-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-405">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-406">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="bcbfc-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-407">Procedures</span></span>  
  
|<span data-ttu-id="bcbfc-408">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-408">ColumnName</span></span>|<span data-ttu-id="bcbfc-409">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="bcbfc-411">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-411">String</span></span>|  
|<span data-ttu-id="bcbfc-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-413">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-413">String</span></span>|  
|<span data-ttu-id="bcbfc-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="bcbfc-415">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-415">String</span></span>|  
|<span data-ttu-id="bcbfc-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="bcbfc-417">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-417">Int16</span></span>|  
|<span data-ttu-id="bcbfc-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="bcbfc-419">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-419">String</span></span>|  
|<span data-ttu-id="bcbfc-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-420">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-421">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-421">String</span></span>|  
|<span data-ttu-id="bcbfc-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-422">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-423">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-424">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="bcbfc-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="bcbfc-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="bcbfc-427">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-427">ColumnName</span></span>|<span data-ttu-id="bcbfc-428">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="bcbfc-430">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-430">String</span></span>|  
|<span data-ttu-id="bcbfc-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-432">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-432">String</span></span>|  
|<span data-ttu-id="bcbfc-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="bcbfc-434">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-434">String</span></span>|  
|<span data-ttu-id="bcbfc-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-435">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-436">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-436">String</span></span>|  
|<span data-ttu-id="bcbfc-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-437">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-438">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-438">Guid</span></span>|  
|<span data-ttu-id="bcbfc-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-439">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-440">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-440">Int64</span></span>|  
|<span data-ttu-id="bcbfc-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="bcbfc-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="bcbfc-442">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-442">Int64</span></span>|  
|<span data-ttu-id="bcbfc-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-444">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-444">Int64</span></span>|  
|<span data-ttu-id="bcbfc-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-445">IS_NULLABLE</span></span>|<span data-ttu-id="bcbfc-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-446">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-447">DATA_TYPE</span></span>|<span data-ttu-id="bcbfc-448">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-448">Int32</span></span>|  
|<span data-ttu-id="bcbfc-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-449">TYPE_GUID</span></span>|<span data-ttu-id="bcbfc-450">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-450">Guid</span></span>|  
|<span data-ttu-id="bcbfc-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="bcbfc-452">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-452">Int64</span></span>|  
|<span data-ttu-id="bcbfc-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="bcbfc-454">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-454">Int64</span></span>|  
|<span data-ttu-id="bcbfc-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="bcbfc-456">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-456">Int32</span></span>|  
|<span data-ttu-id="bcbfc-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="bcbfc-458">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-458">Int16</span></span>|  
|<span data-ttu-id="bcbfc-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-459">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-460">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-460">String</span></span>|  
|<span data-ttu-id="bcbfc-461">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-461">OVERLOAD</span></span>|<span data-ttu-id="bcbfc-462">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="bcbfc-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="bcbfc-463">Views</span></span>  
  
|<span data-ttu-id="bcbfc-464">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-464">ColumnName</span></span>|<span data-ttu-id="bcbfc-465">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-466">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-467">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-467">String</span></span>|  
|<span data-ttu-id="bcbfc-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-469">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-469">String</span></span>|  
|<span data-ttu-id="bcbfc-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-470">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-471">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-471">String</span></span>|  
|<span data-ttu-id="bcbfc-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="bcbfc-473">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-473">String</span></span>|  
|<span data-ttu-id="bcbfc-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-474">CHECK_OPTION</span></span>|<span data-ttu-id="bcbfc-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-475">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-476">IS_UPDATABLE</span></span>|<span data-ttu-id="bcbfc-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-477">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-478">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-479">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-479">String</span></span>|  
|<span data-ttu-id="bcbfc-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-480">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-481">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-482">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="bcbfc-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-484">Indexes</span></span>  
  
|<span data-ttu-id="bcbfc-485">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-485">ColumnName</span></span>|<span data-ttu-id="bcbfc-486">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-487">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-488">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-488">String</span></span>|  
|<span data-ttu-id="bcbfc-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-490">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-490">String</span></span>|  
|<span data-ttu-id="bcbfc-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-491">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-492">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-492">String</span></span>|  
|<span data-ttu-id="bcbfc-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-493">INDEX_CATALOG</span></span>|<span data-ttu-id="bcbfc-494">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-494">String</span></span>|  
|<span data-ttu-id="bcbfc-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="bcbfc-496">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-496">String</span></span>|  
|<span data-ttu-id="bcbfc-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-497">INDEX_NAME</span></span>|<span data-ttu-id="bcbfc-498">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-498">String</span></span>|  
|<span data-ttu-id="bcbfc-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-499">PRIMARY_KEY</span></span>|<span data-ttu-id="bcbfc-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-500">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-501">UNIQUE</span></span>|<span data-ttu-id="bcbfc-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-502">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-503">CLUSTERED</span></span>|<span data-ttu-id="bcbfc-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-504">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-505">TYP</span><span class="sxs-lookup"><span data-stu-id="bcbfc-505">TYPE</span></span>|<span data-ttu-id="bcbfc-506">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-506">Int32</span></span>|  
|<span data-ttu-id="bcbfc-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="bcbfc-507">FILL_FACTOR</span></span>|<span data-ttu-id="bcbfc-508">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-508">Int32</span></span>|  
|<span data-ttu-id="bcbfc-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-509">INITIAL_SIZE</span></span>|<span data-ttu-id="bcbfc-510">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-510">Int32</span></span>|  
|<span data-ttu-id="bcbfc-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="bcbfc-511">NULLS</span></span>|<span data-ttu-id="bcbfc-512">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-512">Int32</span></span>|  
|<span data-ttu-id="bcbfc-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="bcbfc-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-514">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-515">AUTO_UPDATE</span></span>|<span data-ttu-id="bcbfc-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-516">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-517">NULL_COLLATION</span></span>|<span data-ttu-id="bcbfc-518">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-518">Int32</span></span>|  
|<span data-ttu-id="bcbfc-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-520">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-520">Int64</span></span>|  
|<span data-ttu-id="bcbfc-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-521">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-522">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-522">String</span></span>|  
|<span data-ttu-id="bcbfc-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-523">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-524">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-524">Guid</span></span>|  
|<span data-ttu-id="bcbfc-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-525">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-526">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-526">Int64</span></span>|  
|<span data-ttu-id="bcbfc-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-527">COLLATION</span></span>|<span data-ttu-id="bcbfc-528">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-528">Int16</span></span>|  
|<span data-ttu-id="bcbfc-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="bcbfc-529">CARDINALITY</span></span>|<span data-ttu-id="bcbfc-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="bcbfc-530">Decimal</span></span>|  
|<span data-ttu-id="bcbfc-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-531">PAGES</span></span>|<span data-ttu-id="bcbfc-532">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-532">Int32</span></span>|  
|<span data-ttu-id="bcbfc-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-533">FILTER_CONDITION</span></span>|<span data-ttu-id="bcbfc-534">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-534">String</span></span>|  
|<span data-ttu-id="bcbfc-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-535">INTEGRATED</span></span>|<span data-ttu-id="bcbfc-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="bcbfc-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="bcbfc-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="bcbfc-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="bcbfc-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="bcbfc-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-539">Tables</span></span>  
  
-   <span data-ttu-id="bcbfc-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-540">Columns</span></span>  
  
-   <span data-ttu-id="bcbfc-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-541">Procedures</span></span>  
  
-   <span data-ttu-id="bcbfc-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="bcbfc-542">Views</span></span>  
  
-   <span data-ttu-id="bcbfc-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="bcbfc-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="bcbfc-544">Tables</span></span>  
  
|<span data-ttu-id="bcbfc-545">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-545">ColumnName</span></span>|<span data-ttu-id="bcbfc-546">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-547">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-548">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-548">String</span></span>|  
|<span data-ttu-id="bcbfc-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-550">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-550">String</span></span>|  
|<span data-ttu-id="bcbfc-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-551">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-552">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-552">String</span></span>|  
|<span data-ttu-id="bcbfc-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-553">TABLE_TYPE</span></span>|<span data-ttu-id="bcbfc-554">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-554">String</span></span>|  
|<span data-ttu-id="bcbfc-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-555">TABLE_GUID</span></span>|<span data-ttu-id="bcbfc-556">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-556">Guid</span></span>|  
|<span data-ttu-id="bcbfc-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-557">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-558">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-558">String</span></span>|  
|<span data-ttu-id="bcbfc-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-559">TABLE_PROPID</span></span>|<span data-ttu-id="bcbfc-560">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-560">Int64</span></span>|  
|<span data-ttu-id="bcbfc-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-561">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-562">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-563">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="bcbfc-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-565">Columns</span></span>  
  
|<span data-ttu-id="bcbfc-566">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-566">ColumnName</span></span>|<span data-ttu-id="bcbfc-567">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-568">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-569">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-569">String</span></span>|  
|<span data-ttu-id="bcbfc-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-571">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-571">String</span></span>|  
|<span data-ttu-id="bcbfc-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-572">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-573">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-573">String</span></span>|  
|<span data-ttu-id="bcbfc-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-574">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-575">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-575">String</span></span>|  
|<span data-ttu-id="bcbfc-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-576">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-577">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-577">Guid</span></span>|  
|<span data-ttu-id="bcbfc-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-578">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-579">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-579">Int64</span></span>|  
|<span data-ttu-id="bcbfc-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-581">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-581">Int64</span></span>|  
|<span data-ttu-id="bcbfc-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="bcbfc-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-583">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="bcbfc-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="bcbfc-585">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-585">String</span></span>|  
|<span data-ttu-id="bcbfc-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="bcbfc-587">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-587">Int64</span></span>|  
|<span data-ttu-id="bcbfc-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-588">IS_NULLABLE</span></span>|<span data-ttu-id="bcbfc-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-589">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-590">DATA_TYPE</span></span>|<span data-ttu-id="bcbfc-591">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-591">Int32</span></span>|  
|<span data-ttu-id="bcbfc-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-592">TYPE_GUID</span></span>|<span data-ttu-id="bcbfc-593">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-593">Guid</span></span>|  
|<span data-ttu-id="bcbfc-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="bcbfc-595">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-595">Int64</span></span>|  
|<span data-ttu-id="bcbfc-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="bcbfc-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="bcbfc-597">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-597">Int64</span></span>|  
|<span data-ttu-id="bcbfc-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="bcbfc-599">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-599">Int32</span></span>|  
|<span data-ttu-id="bcbfc-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="bcbfc-601">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-601">Int16</span></span>|  
|<span data-ttu-id="bcbfc-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="bcbfc-603">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-603">Int64</span></span>|  
|<span data-ttu-id="bcbfc-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="bcbfc-605">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-605">String</span></span>|  
|<span data-ttu-id="bcbfc-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="bcbfc-607">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-607">String</span></span>|  
|<span data-ttu-id="bcbfc-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="bcbfc-609">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-609">String</span></span>|  
|<span data-ttu-id="bcbfc-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="bcbfc-611">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-611">String</span></span>|  
|<span data-ttu-id="bcbfc-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="bcbfc-613">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-613">String</span></span>|  
|<span data-ttu-id="bcbfc-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-614">COLLATION_NAME</span></span>|<span data-ttu-id="bcbfc-615">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-615">String</span></span>|  
|<span data-ttu-id="bcbfc-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="bcbfc-617">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-617">String</span></span>|  
|<span data-ttu-id="bcbfc-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="bcbfc-619">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-619">String</span></span>|  
|<span data-ttu-id="bcbfc-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-620">DOMAIN_NAME</span></span>|<span data-ttu-id="bcbfc-621">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-621">String</span></span>|  
|<span data-ttu-id="bcbfc-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-622">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-623">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="bcbfc-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="bcbfc-624">Procedures</span></span>  
  
|<span data-ttu-id="bcbfc-625">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-625">ColumnName</span></span>|<span data-ttu-id="bcbfc-626">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="bcbfc-628">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-628">String</span></span>|  
|<span data-ttu-id="bcbfc-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-630">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-630">String</span></span>|  
|<span data-ttu-id="bcbfc-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="bcbfc-632">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-632">String</span></span>|  
|<span data-ttu-id="bcbfc-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="bcbfc-634">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-634">Int16</span></span>|  
|<span data-ttu-id="bcbfc-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="bcbfc-636">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-636">String</span></span>|  
|<span data-ttu-id="bcbfc-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-637">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-638">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-638">String</span></span>|  
|<span data-ttu-id="bcbfc-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-639">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-640">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-641">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="bcbfc-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="bcbfc-643">Views</span></span>  
  
|<span data-ttu-id="bcbfc-644">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-644">ColumnName</span></span>|<span data-ttu-id="bcbfc-645">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-646">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-647">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-647">String</span></span>|  
|<span data-ttu-id="bcbfc-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-649">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-649">String</span></span>|  
|<span data-ttu-id="bcbfc-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-650">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-651">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-651">String</span></span>|  
|<span data-ttu-id="bcbfc-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="bcbfc-653">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-653">String</span></span>|  
|<span data-ttu-id="bcbfc-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-654">CHECK_OPTION</span></span>|<span data-ttu-id="bcbfc-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-655">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-656">IS_UPDATABLE</span></span>|<span data-ttu-id="bcbfc-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-657">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="bcbfc-658">DESCRIPTION</span></span>|<span data-ttu-id="bcbfc-659">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-659">String</span></span>|  
|<span data-ttu-id="bcbfc-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-660">DATE_CREATED</span></span>|<span data-ttu-id="bcbfc-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-661">DateTime</span></span>|  
|<span data-ttu-id="bcbfc-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-662">DATE_MODIFIED</span></span>|<span data-ttu-id="bcbfc-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="bcbfc-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="bcbfc-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="bcbfc-664">Indexes</span></span>  
  
|<span data-ttu-id="bcbfc-665">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="bcbfc-665">ColumnName</span></span>|<span data-ttu-id="bcbfc-666">DataType</span><span class="sxs-lookup"><span data-stu-id="bcbfc-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="bcbfc-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-667">TABLE_CATALOG</span></span>|<span data-ttu-id="bcbfc-668">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-668">String</span></span>|  
|<span data-ttu-id="bcbfc-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="bcbfc-670">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-670">String</span></span>|  
|<span data-ttu-id="bcbfc-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-671">TABLE_NAME</span></span>|<span data-ttu-id="bcbfc-672">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-672">String</span></span>|  
|<span data-ttu-id="bcbfc-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bcbfc-673">INDEX_CATALOG</span></span>|<span data-ttu-id="bcbfc-674">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-674">String</span></span>|  
|<span data-ttu-id="bcbfc-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="bcbfc-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="bcbfc-676">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-676">String</span></span>|  
|<span data-ttu-id="bcbfc-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-677">INDEX_NAME</span></span>|<span data-ttu-id="bcbfc-678">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-678">String</span></span>|  
|<span data-ttu-id="bcbfc-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-679">PRIMARY_KEY</span></span>|<span data-ttu-id="bcbfc-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-680">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-681">UNIQUE</span></span>|<span data-ttu-id="bcbfc-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-682">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-683">CLUSTERED</span></span>|<span data-ttu-id="bcbfc-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-684">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-685">TYP</span><span class="sxs-lookup"><span data-stu-id="bcbfc-685">TYPE</span></span>|<span data-ttu-id="bcbfc-686">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-686">Int32</span></span>|  
|<span data-ttu-id="bcbfc-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="bcbfc-687">FILL_FACTOR</span></span>|<span data-ttu-id="bcbfc-688">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-688">Int32</span></span>|  
|<span data-ttu-id="bcbfc-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-689">INITIAL_SIZE</span></span>|<span data-ttu-id="bcbfc-690">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-690">Int32</span></span>|  
|<span data-ttu-id="bcbfc-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="bcbfc-691">NULLS</span></span>|<span data-ttu-id="bcbfc-692">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-692">Int32</span></span>|  
|<span data-ttu-id="bcbfc-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="bcbfc-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="bcbfc-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-694">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-695">AUTO_UPDATE</span></span>|<span data-ttu-id="bcbfc-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-696">Boolean</span></span>|  
|<span data-ttu-id="bcbfc-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-697">NULL_COLLATION</span></span>|<span data-ttu-id="bcbfc-698">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-698">Int32</span></span>|  
|<span data-ttu-id="bcbfc-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="bcbfc-700">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-700">Int64</span></span>|  
|<span data-ttu-id="bcbfc-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="bcbfc-701">COLUMN_NAME</span></span>|<span data-ttu-id="bcbfc-702">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-702">String</span></span>|  
|<span data-ttu-id="bcbfc-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-703">COLUMN_GUID</span></span>|<span data-ttu-id="bcbfc-704">Guid</span><span class="sxs-lookup"><span data-stu-id="bcbfc-704">Guid</span></span>|  
|<span data-ttu-id="bcbfc-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="bcbfc-705">COLUMN_PROPID</span></span>|<span data-ttu-id="bcbfc-706">Int64</span><span class="sxs-lookup"><span data-stu-id="bcbfc-706">Int64</span></span>|  
|<span data-ttu-id="bcbfc-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="bcbfc-707">COLLATION</span></span>|<span data-ttu-id="bcbfc-708">Int16</span><span class="sxs-lookup"><span data-stu-id="bcbfc-708">Int16</span></span>|  
|<span data-ttu-id="bcbfc-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="bcbfc-709">CARDINALITY</span></span>|<span data-ttu-id="bcbfc-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="bcbfc-710">Decimal</span></span>|  
|<span data-ttu-id="bcbfc-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="bcbfc-711">PAGES</span></span>|<span data-ttu-id="bcbfc-712">Int32</span><span class="sxs-lookup"><span data-stu-id="bcbfc-712">Int32</span></span>|  
|<span data-ttu-id="bcbfc-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="bcbfc-713">FILTER_CONDITION</span></span>|<span data-ttu-id="bcbfc-714">String</span><span class="sxs-lookup"><span data-stu-id="bcbfc-714">String</span></span>|  
|<span data-ttu-id="bcbfc-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="bcbfc-715">INTEGRATED</span></span>|<span data-ttu-id="bcbfc-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="bcbfc-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcbfc-717">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcbfc-717">See also</span></span>

- [<span data-ttu-id="bcbfc-718">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="bcbfc-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
