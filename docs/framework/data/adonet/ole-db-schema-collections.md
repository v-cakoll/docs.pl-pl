---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164687"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="b1354-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="b1354-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="b1354-103">W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="b1354-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="b1354-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="b1354-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="b1354-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b1354-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b1354-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-106">Tables</span></span>  
  
-   <span data-ttu-id="b1354-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-107">Columns</span></span>  
  
-   <span data-ttu-id="b1354-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-108">Procedures</span></span>  
  
-   <span data-ttu-id="b1354-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1354-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b1354-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="b1354-110">Catalog</span></span>  
  
-   <span data-ttu-id="b1354-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1354-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-112">Tables</span></span>  
  
|<span data-ttu-id="b1354-113">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-113">ColumnName</span></span>|<span data-ttu-id="b1354-114">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-115">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-116">String</span><span class="sxs-lookup"><span data-stu-id="b1354-116">String</span></span>|  
|<span data-ttu-id="b1354-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-118">String</span><span class="sxs-lookup"><span data-stu-id="b1354-118">String</span></span>|  
|<span data-ttu-id="b1354-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-119">TABLE_NAME</span></span>|<span data-ttu-id="b1354-120">String</span><span class="sxs-lookup"><span data-stu-id="b1354-120">String</span></span>|  
|<span data-ttu-id="b1354-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-121">TABLE_TYPE</span></span>|<span data-ttu-id="b1354-122">String</span><span class="sxs-lookup"><span data-stu-id="b1354-122">String</span></span>|  
|<span data-ttu-id="b1354-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-123">TABLE_GUID</span></span>|<span data-ttu-id="b1354-124">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-124">Guid</span></span>|  
|<span data-ttu-id="b1354-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-125">DESCRIPTION</span></span>|<span data-ttu-id="b1354-126">String</span><span class="sxs-lookup"><span data-stu-id="b1354-126">String</span></span>|  
|<span data-ttu-id="b1354-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-127">TABLE_PROPID</span></span>|<span data-ttu-id="b1354-128">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-128">Int64</span></span>|  
|<span data-ttu-id="b1354-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-129">DATE_CREATED</span></span>|<span data-ttu-id="b1354-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-130">DateTime</span></span>|  
|<span data-ttu-id="b1354-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-131">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1354-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-133">Columns</span></span>  
  
|<span data-ttu-id="b1354-134">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-134">ColumnName</span></span>|<span data-ttu-id="b1354-135">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-136">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-137">String</span><span class="sxs-lookup"><span data-stu-id="b1354-137">String</span></span>|  
|<span data-ttu-id="b1354-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-139">String</span><span class="sxs-lookup"><span data-stu-id="b1354-139">String</span></span>|  
|<span data-ttu-id="b1354-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-140">TABLE_NAME</span></span>|<span data-ttu-id="b1354-141">String</span><span class="sxs-lookup"><span data-stu-id="b1354-141">String</span></span>|  
|<span data-ttu-id="b1354-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-142">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-143">String</span><span class="sxs-lookup"><span data-stu-id="b1354-143">String</span></span>|  
|<span data-ttu-id="b1354-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-144">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-145">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-145">Guid</span></span>|  
|<span data-ttu-id="b1354-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-146">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-147">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-147">Int64</span></span>|  
|<span data-ttu-id="b1354-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-149">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-149">Int64</span></span>|  
|<span data-ttu-id="b1354-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1354-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-151">Boolean</span></span>|  
|<span data-ttu-id="b1354-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1354-153">String</span><span class="sxs-lookup"><span data-stu-id="b1354-153">String</span></span>|  
|<span data-ttu-id="b1354-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1354-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1354-155">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-155">Int64</span></span>|  
|<span data-ttu-id="b1354-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-156">IS_NULLABLE</span></span>|<span data-ttu-id="b1354-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-157">Boolean</span></span>|  
|<span data-ttu-id="b1354-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-158">DATA_TYPE</span></span>|<span data-ttu-id="b1354-159">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-159">Int32</span></span>|  
|<span data-ttu-id="b1354-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-160">TYPE_GUID</span></span>|<span data-ttu-id="b1354-161">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-161">Guid</span></span>|  
|<span data-ttu-id="b1354-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1354-163">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-163">Int64</span></span>|  
|<span data-ttu-id="b1354-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1354-165">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-165">Int64</span></span>|  
|<span data-ttu-id="b1354-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1354-167">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-167">Int32</span></span>|  
|<span data-ttu-id="b1354-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1354-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1354-169">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-169">Int16</span></span>|  
|<span data-ttu-id="b1354-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1354-171">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-171">Int64</span></span>|  
|<span data-ttu-id="b1354-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1354-173">String</span><span class="sxs-lookup"><span data-stu-id="b1354-173">String</span></span>|  
|<span data-ttu-id="b1354-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1354-175">String</span><span class="sxs-lookup"><span data-stu-id="b1354-175">String</span></span>|  
|<span data-ttu-id="b1354-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1354-177">String</span><span class="sxs-lookup"><span data-stu-id="b1354-177">String</span></span>|  
|<span data-ttu-id="b1354-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1354-179">String</span><span class="sxs-lookup"><span data-stu-id="b1354-179">String</span></span>|  
|<span data-ttu-id="b1354-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1354-181">String</span><span class="sxs-lookup"><span data-stu-id="b1354-181">String</span></span>|  
|<span data-ttu-id="b1354-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-182">COLLATION_NAME</span></span>|<span data-ttu-id="b1354-183">String</span><span class="sxs-lookup"><span data-stu-id="b1354-183">String</span></span>|  
|<span data-ttu-id="b1354-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1354-185">String</span><span class="sxs-lookup"><span data-stu-id="b1354-185">String</span></span>|  
|<span data-ttu-id="b1354-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1354-187">String</span><span class="sxs-lookup"><span data-stu-id="b1354-187">String</span></span>|  
|<span data-ttu-id="b1354-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-188">DOMAIN_NAME</span></span>|<span data-ttu-id="b1354-189">String</span><span class="sxs-lookup"><span data-stu-id="b1354-189">String</span></span>|  
|<span data-ttu-id="b1354-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-190">DESCRIPTION</span></span>|<span data-ttu-id="b1354-191">String</span><span class="sxs-lookup"><span data-stu-id="b1354-191">String</span></span>|  
|<span data-ttu-id="b1354-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="b1354-192">COLUMN_LCID</span></span>|<span data-ttu-id="b1354-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-193">Int32</span></span>|  
|<span data-ttu-id="b1354-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="b1354-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="b1354-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-195">Int32</span></span>|  
|<span data-ttu-id="b1354-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="b1354-196">COLUMN_SORTID</span></span>|<span data-ttu-id="b1354-197">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-197">Int32</span></span>|  
|<span data-ttu-id="b1354-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="b1354-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="b1354-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="b1354-199">Byte[]</span></span>|  
|<span data-ttu-id="b1354-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="b1354-200">IS_COMPUTED</span></span>|<span data-ttu-id="b1354-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1354-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-202">Procedures</span></span>  
  
|<span data-ttu-id="b1354-203">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-203">ColumnName</span></span>|<span data-ttu-id="b1354-204">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1354-206">String</span><span class="sxs-lookup"><span data-stu-id="b1354-206">String</span></span>|  
|<span data-ttu-id="b1354-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1354-208">String</span><span class="sxs-lookup"><span data-stu-id="b1354-208">String</span></span>|  
|<span data-ttu-id="b1354-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1354-210">String</span><span class="sxs-lookup"><span data-stu-id="b1354-210">String</span></span>|  
|<span data-ttu-id="b1354-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1354-212">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-212">Int16</span></span>|  
|<span data-ttu-id="b1354-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1354-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1354-214">String</span><span class="sxs-lookup"><span data-stu-id="b1354-214">String</span></span>|  
|<span data-ttu-id="b1354-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-215">DESCRIPTION</span></span>|<span data-ttu-id="b1354-216">String</span><span class="sxs-lookup"><span data-stu-id="b1354-216">String</span></span>|  
|<span data-ttu-id="b1354-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-217">DATE_CREATED</span></span>|<span data-ttu-id="b1354-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-218">DateTime</span></span>|  
|<span data-ttu-id="b1354-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-219">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b1354-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1354-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b1354-222">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-222">ColumnName</span></span>|<span data-ttu-id="b1354-223">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1354-225">String</span><span class="sxs-lookup"><span data-stu-id="b1354-225">String</span></span>|  
|<span data-ttu-id="b1354-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1354-227">String</span><span class="sxs-lookup"><span data-stu-id="b1354-227">String</span></span>|  
|<span data-ttu-id="b1354-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1354-229">String</span><span class="sxs-lookup"><span data-stu-id="b1354-229">String</span></span>|  
|<span data-ttu-id="b1354-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-230">PARAMETER_NAME</span></span>|<span data-ttu-id="b1354-231">String</span><span class="sxs-lookup"><span data-stu-id="b1354-231">String</span></span>|  
|<span data-ttu-id="b1354-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-233">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-233">Int32</span></span>|  
|<span data-ttu-id="b1354-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="b1354-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="b1354-235">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-235">Int32</span></span>|  
|<span data-ttu-id="b1354-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="b1354-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-237">Boolean</span></span>|  
|<span data-ttu-id="b1354-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="b1354-239">String</span><span class="sxs-lookup"><span data-stu-id="b1354-239">String</span></span>|  
|<span data-ttu-id="b1354-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-240">IS_NULLABLE</span></span>|<span data-ttu-id="b1354-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-241">Boolean</span></span>|  
|<span data-ttu-id="b1354-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-242">DATA_TYPE</span></span>|<span data-ttu-id="b1354-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-243">Int32</span></span>|  
|<span data-ttu-id="b1354-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1354-245">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-245">Int64</span></span>|  
|<span data-ttu-id="b1354-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1354-247">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-247">Int64</span></span>|  
|<span data-ttu-id="b1354-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1354-249">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-249">Int32</span></span>|  
|<span data-ttu-id="b1354-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1354-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1354-251">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-251">Int16</span></span>|  
|<span data-ttu-id="b1354-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-252">DESCRIPTION</span></span>|<span data-ttu-id="b1354-253">String</span><span class="sxs-lookup"><span data-stu-id="b1354-253">String</span></span>|  
|<span data-ttu-id="b1354-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-254">TYPE_NAME</span></span>|<span data-ttu-id="b1354-255">String</span><span class="sxs-lookup"><span data-stu-id="b1354-255">String</span></span>|  
|<span data-ttu-id="b1354-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="b1354-257">String</span><span class="sxs-lookup"><span data-stu-id="b1354-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="b1354-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="b1354-258">Catalog</span></span>  
  
|<span data-ttu-id="b1354-259">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-259">ColumnName</span></span>|<span data-ttu-id="b1354-260">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-261">CATALOG_NAME</span></span>|<span data-ttu-id="b1354-262">String</span><span class="sxs-lookup"><span data-stu-id="b1354-262">String</span></span>|  
|<span data-ttu-id="b1354-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-263">DESCRIPTION</span></span>|<span data-ttu-id="b1354-264">String</span><span class="sxs-lookup"><span data-stu-id="b1354-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1354-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-265">Indexes</span></span>  
  
|<span data-ttu-id="b1354-266">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-266">ColumnName</span></span>|<span data-ttu-id="b1354-267">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-268">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-269">String</span><span class="sxs-lookup"><span data-stu-id="b1354-269">String</span></span>|  
|<span data-ttu-id="b1354-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-271">String</span><span class="sxs-lookup"><span data-stu-id="b1354-271">String</span></span>|  
|<span data-ttu-id="b1354-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-272">TABLE_NAME</span></span>|<span data-ttu-id="b1354-273">String</span><span class="sxs-lookup"><span data-stu-id="b1354-273">String</span></span>|  
|<span data-ttu-id="b1354-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-274">INDEX_CATALOG</span></span>|<span data-ttu-id="b1354-275">String</span><span class="sxs-lookup"><span data-stu-id="b1354-275">String</span></span>|  
|<span data-ttu-id="b1354-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1354-277">String</span><span class="sxs-lookup"><span data-stu-id="b1354-277">String</span></span>|  
|<span data-ttu-id="b1354-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-278">INDEX_NAME</span></span>|<span data-ttu-id="b1354-279">String</span><span class="sxs-lookup"><span data-stu-id="b1354-279">String</span></span>|  
|<span data-ttu-id="b1354-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1354-280">PRIMARY_KEY</span></span>|<span data-ttu-id="b1354-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-281">Boolean</span></span>|  
|<span data-ttu-id="b1354-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1354-282">UNIQUE</span></span>|<span data-ttu-id="b1354-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-283">Boolean</span></span>|  
|<span data-ttu-id="b1354-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1354-284">CLUSTERED</span></span>|<span data-ttu-id="b1354-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-285">Boolean</span></span>|  
|<span data-ttu-id="b1354-286">TYP</span><span class="sxs-lookup"><span data-stu-id="b1354-286">TYPE</span></span>|<span data-ttu-id="b1354-287">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-287">Int32</span></span>|  
|<span data-ttu-id="b1354-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1354-288">FILL_FACTOR</span></span>|<span data-ttu-id="b1354-289">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-289">Int32</span></span>|  
|<span data-ttu-id="b1354-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1354-290">INITIAL_SIZE</span></span>|<span data-ttu-id="b1354-291">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-291">Int32</span></span>|  
|<span data-ttu-id="b1354-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="b1354-292">NULLS</span></span>|<span data-ttu-id="b1354-293">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-293">Int32</span></span>|  
|<span data-ttu-id="b1354-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1354-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1354-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-295">Boolean</span></span>|  
|<span data-ttu-id="b1354-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1354-296">AUTO_UPDATE</span></span>|<span data-ttu-id="b1354-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-297">Boolean</span></span>|  
|<span data-ttu-id="b1354-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1354-298">NULL_COLLATION</span></span>|<span data-ttu-id="b1354-299">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-299">Int32</span></span>|  
|<span data-ttu-id="b1354-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-301">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-301">Int64</span></span>|  
|<span data-ttu-id="b1354-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-302">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-303">String</span><span class="sxs-lookup"><span data-stu-id="b1354-303">String</span></span>|  
|<span data-ttu-id="b1354-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-304">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-305">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-305">Guid</span></span>|  
|<span data-ttu-id="b1354-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-306">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-307">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-307">Int64</span></span>|  
|<span data-ttu-id="b1354-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="b1354-308">COLLATION</span></span>|<span data-ttu-id="b1354-309">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-309">Int16</span></span>|  
|<span data-ttu-id="b1354-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b1354-310">CARDINALITY</span></span>|<span data-ttu-id="b1354-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="b1354-311">Decimal</span></span>|  
|<span data-ttu-id="b1354-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="b1354-312">PAGES</span></span>|<span data-ttu-id="b1354-313">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-313">Int32</span></span>|  
|<span data-ttu-id="b1354-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1354-314">FILTER_CONDITION</span></span>|<span data-ttu-id="b1354-315">String</span><span class="sxs-lookup"><span data-stu-id="b1354-315">String</span></span>|  
|<span data-ttu-id="b1354-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1354-316">INTEGRATED</span></span>|<span data-ttu-id="b1354-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="b1354-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="b1354-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="b1354-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b1354-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b1354-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-320">Tables</span></span>  
  
-   <span data-ttu-id="b1354-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-321">Columns</span></span>  
  
-   <span data-ttu-id="b1354-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-322">Procedures</span></span>  
  
-   <span data-ttu-id="b1354-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b1354-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b1354-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b1354-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b1354-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="b1354-325">Views</span></span>  
  
-   <span data-ttu-id="b1354-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1354-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-327">Tables</span></span>  
  
|<span data-ttu-id="b1354-328">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-328">ColumnName</span></span>|<span data-ttu-id="b1354-329">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-330">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-331">String</span><span class="sxs-lookup"><span data-stu-id="b1354-331">String</span></span>|  
|<span data-ttu-id="b1354-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-333">String</span><span class="sxs-lookup"><span data-stu-id="b1354-333">String</span></span>|  
|<span data-ttu-id="b1354-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-334">TABLE_NAME</span></span>|<span data-ttu-id="b1354-335">String</span><span class="sxs-lookup"><span data-stu-id="b1354-335">String</span></span>|  
|<span data-ttu-id="b1354-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-336">TABLE_TYPE</span></span>|<span data-ttu-id="b1354-337">String</span><span class="sxs-lookup"><span data-stu-id="b1354-337">String</span></span>|  
|<span data-ttu-id="b1354-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-338">TABLE_GUID</span></span>|<span data-ttu-id="b1354-339">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-339">Guid</span></span>|  
|<span data-ttu-id="b1354-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-340">DESCRIPTION</span></span>|<span data-ttu-id="b1354-341">String</span><span class="sxs-lookup"><span data-stu-id="b1354-341">String</span></span>|  
|<span data-ttu-id="b1354-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-342">TABLE_PROPID</span></span>|<span data-ttu-id="b1354-343">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-343">Int64</span></span>|  
|<span data-ttu-id="b1354-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-344">DATE_CREATED</span></span>|<span data-ttu-id="b1354-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-345">DateTime</span></span>|  
|<span data-ttu-id="b1354-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-346">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1354-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-348">Columns</span></span>  
  
|<span data-ttu-id="b1354-349">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-349">ColumnName</span></span>|<span data-ttu-id="b1354-350">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-351">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-352">String</span><span class="sxs-lookup"><span data-stu-id="b1354-352">String</span></span>|  
|<span data-ttu-id="b1354-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-354">String</span><span class="sxs-lookup"><span data-stu-id="b1354-354">String</span></span>|  
|<span data-ttu-id="b1354-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-355">TABLE_NAME</span></span>|<span data-ttu-id="b1354-356">String</span><span class="sxs-lookup"><span data-stu-id="b1354-356">String</span></span>|  
|<span data-ttu-id="b1354-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-357">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-358">String</span><span class="sxs-lookup"><span data-stu-id="b1354-358">String</span></span>|  
|<span data-ttu-id="b1354-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-359">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-360">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-360">Guid</span></span>|  
|<span data-ttu-id="b1354-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-361">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-362">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-362">Int64</span></span>|  
|<span data-ttu-id="b1354-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-364">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-364">Int64</span></span>|  
|<span data-ttu-id="b1354-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1354-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-366">Boolean</span></span>|  
|<span data-ttu-id="b1354-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1354-368">String</span><span class="sxs-lookup"><span data-stu-id="b1354-368">String</span></span>|  
|<span data-ttu-id="b1354-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1354-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1354-370">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-370">Int64</span></span>|  
|<span data-ttu-id="b1354-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-371">IS_NULLABLE</span></span>|<span data-ttu-id="b1354-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-372">Boolean</span></span>|  
|<span data-ttu-id="b1354-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-373">DATA_TYPE</span></span>|<span data-ttu-id="b1354-374">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-374">Int32</span></span>|  
|<span data-ttu-id="b1354-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-375">TYPE_GUID</span></span>|<span data-ttu-id="b1354-376">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-376">Guid</span></span>|  
|<span data-ttu-id="b1354-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1354-378">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-378">Int64</span></span>|  
|<span data-ttu-id="b1354-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1354-380">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-380">Int64</span></span>|  
|<span data-ttu-id="b1354-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1354-382">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-382">Int32</span></span>|  
|<span data-ttu-id="b1354-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1354-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1354-384">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-384">Int16</span></span>|  
|<span data-ttu-id="b1354-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1354-386">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-386">Int64</span></span>|  
|<span data-ttu-id="b1354-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1354-388">String</span><span class="sxs-lookup"><span data-stu-id="b1354-388">String</span></span>|  
|<span data-ttu-id="b1354-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1354-390">String</span><span class="sxs-lookup"><span data-stu-id="b1354-390">String</span></span>|  
|<span data-ttu-id="b1354-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1354-392">String</span><span class="sxs-lookup"><span data-stu-id="b1354-392">String</span></span>|  
|<span data-ttu-id="b1354-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1354-394">String</span><span class="sxs-lookup"><span data-stu-id="b1354-394">String</span></span>|  
|<span data-ttu-id="b1354-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1354-396">String</span><span class="sxs-lookup"><span data-stu-id="b1354-396">String</span></span>|  
|<span data-ttu-id="b1354-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-397">COLLATION_NAME</span></span>|<span data-ttu-id="b1354-398">String</span><span class="sxs-lookup"><span data-stu-id="b1354-398">String</span></span>|  
|<span data-ttu-id="b1354-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1354-400">String</span><span class="sxs-lookup"><span data-stu-id="b1354-400">String</span></span>|  
|<span data-ttu-id="b1354-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1354-402">String</span><span class="sxs-lookup"><span data-stu-id="b1354-402">String</span></span>|  
|<span data-ttu-id="b1354-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-403">DOMAIN_NAME</span></span>|<span data-ttu-id="b1354-404">String</span><span class="sxs-lookup"><span data-stu-id="b1354-404">String</span></span>|  
|<span data-ttu-id="b1354-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-405">DESCRIPTION</span></span>|<span data-ttu-id="b1354-406">String</span><span class="sxs-lookup"><span data-stu-id="b1354-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1354-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-407">Procedures</span></span>  
  
|<span data-ttu-id="b1354-408">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-408">ColumnName</span></span>|<span data-ttu-id="b1354-409">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1354-411">String</span><span class="sxs-lookup"><span data-stu-id="b1354-411">String</span></span>|  
|<span data-ttu-id="b1354-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1354-413">String</span><span class="sxs-lookup"><span data-stu-id="b1354-413">String</span></span>|  
|<span data-ttu-id="b1354-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1354-415">String</span><span class="sxs-lookup"><span data-stu-id="b1354-415">String</span></span>|  
|<span data-ttu-id="b1354-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1354-417">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-417">Int16</span></span>|  
|<span data-ttu-id="b1354-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1354-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1354-419">String</span><span class="sxs-lookup"><span data-stu-id="b1354-419">String</span></span>|  
|<span data-ttu-id="b1354-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-420">DESCRIPTION</span></span>|<span data-ttu-id="b1354-421">String</span><span class="sxs-lookup"><span data-stu-id="b1354-421">String</span></span>|  
|<span data-ttu-id="b1354-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-422">DATE_CREATED</span></span>|<span data-ttu-id="b1354-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-423">DateTime</span></span>|  
|<span data-ttu-id="b1354-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-424">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b1354-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b1354-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b1354-427">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-427">ColumnName</span></span>|<span data-ttu-id="b1354-428">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1354-430">String</span><span class="sxs-lookup"><span data-stu-id="b1354-430">String</span></span>|  
|<span data-ttu-id="b1354-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1354-432">String</span><span class="sxs-lookup"><span data-stu-id="b1354-432">String</span></span>|  
|<span data-ttu-id="b1354-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1354-434">String</span><span class="sxs-lookup"><span data-stu-id="b1354-434">String</span></span>|  
|<span data-ttu-id="b1354-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-435">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-436">String</span><span class="sxs-lookup"><span data-stu-id="b1354-436">String</span></span>|  
|<span data-ttu-id="b1354-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-437">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-438">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-438">Guid</span></span>|  
|<span data-ttu-id="b1354-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-439">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-440">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-440">Int64</span></span>|  
|<span data-ttu-id="b1354-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="b1354-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="b1354-442">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-442">Int64</span></span>|  
|<span data-ttu-id="b1354-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-444">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-444">Int64</span></span>|  
|<span data-ttu-id="b1354-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-445">IS_NULLABLE</span></span>|<span data-ttu-id="b1354-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-446">Boolean</span></span>|  
|<span data-ttu-id="b1354-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-447">DATA_TYPE</span></span>|<span data-ttu-id="b1354-448">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-448">Int32</span></span>|  
|<span data-ttu-id="b1354-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-449">TYPE_GUID</span></span>|<span data-ttu-id="b1354-450">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-450">Guid</span></span>|  
|<span data-ttu-id="b1354-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1354-452">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-452">Int64</span></span>|  
|<span data-ttu-id="b1354-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1354-454">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-454">Int64</span></span>|  
|<span data-ttu-id="b1354-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1354-456">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-456">Int32</span></span>|  
|<span data-ttu-id="b1354-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1354-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1354-458">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-458">Int16</span></span>|  
|<span data-ttu-id="b1354-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-459">DESCRIPTION</span></span>|<span data-ttu-id="b1354-460">String</span><span class="sxs-lookup"><span data-stu-id="b1354-460">String</span></span>|  
|<span data-ttu-id="b1354-461">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="b1354-461">OVERLOAD</span></span>|<span data-ttu-id="b1354-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b1354-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="b1354-463">Views</span></span>  
  
|<span data-ttu-id="b1354-464">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-464">ColumnName</span></span>|<span data-ttu-id="b1354-465">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-466">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-467">String</span><span class="sxs-lookup"><span data-stu-id="b1354-467">String</span></span>|  
|<span data-ttu-id="b1354-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-469">String</span><span class="sxs-lookup"><span data-stu-id="b1354-469">String</span></span>|  
|<span data-ttu-id="b1354-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-470">TABLE_NAME</span></span>|<span data-ttu-id="b1354-471">String</span><span class="sxs-lookup"><span data-stu-id="b1354-471">String</span></span>|  
|<span data-ttu-id="b1354-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1354-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="b1354-473">String</span><span class="sxs-lookup"><span data-stu-id="b1354-473">String</span></span>|  
|<span data-ttu-id="b1354-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b1354-474">CHECK_OPTION</span></span>|<span data-ttu-id="b1354-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-475">Boolean</span></span>|  
|<span data-ttu-id="b1354-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-476">IS_UPDATABLE</span></span>|<span data-ttu-id="b1354-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-477">Boolean</span></span>|  
|<span data-ttu-id="b1354-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-478">DESCRIPTION</span></span>|<span data-ttu-id="b1354-479">String</span><span class="sxs-lookup"><span data-stu-id="b1354-479">String</span></span>|  
|<span data-ttu-id="b1354-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-480">DATE_CREATED</span></span>|<span data-ttu-id="b1354-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-481">DateTime</span></span>|  
|<span data-ttu-id="b1354-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-482">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1354-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-484">Indexes</span></span>  
  
|<span data-ttu-id="b1354-485">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-485">ColumnName</span></span>|<span data-ttu-id="b1354-486">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-487">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-488">String</span><span class="sxs-lookup"><span data-stu-id="b1354-488">String</span></span>|  
|<span data-ttu-id="b1354-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-490">String</span><span class="sxs-lookup"><span data-stu-id="b1354-490">String</span></span>|  
|<span data-ttu-id="b1354-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-491">TABLE_NAME</span></span>|<span data-ttu-id="b1354-492">String</span><span class="sxs-lookup"><span data-stu-id="b1354-492">String</span></span>|  
|<span data-ttu-id="b1354-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-493">INDEX_CATALOG</span></span>|<span data-ttu-id="b1354-494">String</span><span class="sxs-lookup"><span data-stu-id="b1354-494">String</span></span>|  
|<span data-ttu-id="b1354-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1354-496">String</span><span class="sxs-lookup"><span data-stu-id="b1354-496">String</span></span>|  
|<span data-ttu-id="b1354-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-497">INDEX_NAME</span></span>|<span data-ttu-id="b1354-498">String</span><span class="sxs-lookup"><span data-stu-id="b1354-498">String</span></span>|  
|<span data-ttu-id="b1354-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1354-499">PRIMARY_KEY</span></span>|<span data-ttu-id="b1354-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-500">Boolean</span></span>|  
|<span data-ttu-id="b1354-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1354-501">UNIQUE</span></span>|<span data-ttu-id="b1354-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-502">Boolean</span></span>|  
|<span data-ttu-id="b1354-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1354-503">CLUSTERED</span></span>|<span data-ttu-id="b1354-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-504">Boolean</span></span>|  
|<span data-ttu-id="b1354-505">TYP</span><span class="sxs-lookup"><span data-stu-id="b1354-505">TYPE</span></span>|<span data-ttu-id="b1354-506">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-506">Int32</span></span>|  
|<span data-ttu-id="b1354-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1354-507">FILL_FACTOR</span></span>|<span data-ttu-id="b1354-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-508">Int32</span></span>|  
|<span data-ttu-id="b1354-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1354-509">INITIAL_SIZE</span></span>|<span data-ttu-id="b1354-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-510">Int32</span></span>|  
|<span data-ttu-id="b1354-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="b1354-511">NULLS</span></span>|<span data-ttu-id="b1354-512">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-512">Int32</span></span>|  
|<span data-ttu-id="b1354-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1354-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1354-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-514">Boolean</span></span>|  
|<span data-ttu-id="b1354-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1354-515">AUTO_UPDATE</span></span>|<span data-ttu-id="b1354-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-516">Boolean</span></span>|  
|<span data-ttu-id="b1354-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1354-517">NULL_COLLATION</span></span>|<span data-ttu-id="b1354-518">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-518">Int32</span></span>|  
|<span data-ttu-id="b1354-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-520">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-520">Int64</span></span>|  
|<span data-ttu-id="b1354-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-521">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-522">String</span><span class="sxs-lookup"><span data-stu-id="b1354-522">String</span></span>|  
|<span data-ttu-id="b1354-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-523">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-524">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-524">Guid</span></span>|  
|<span data-ttu-id="b1354-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-525">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-526">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-526">Int64</span></span>|  
|<span data-ttu-id="b1354-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="b1354-527">COLLATION</span></span>|<span data-ttu-id="b1354-528">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-528">Int16</span></span>|  
|<span data-ttu-id="b1354-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b1354-529">CARDINALITY</span></span>|<span data-ttu-id="b1354-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="b1354-530">Decimal</span></span>|  
|<span data-ttu-id="b1354-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="b1354-531">PAGES</span></span>|<span data-ttu-id="b1354-532">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-532">Int32</span></span>|  
|<span data-ttu-id="b1354-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1354-533">FILTER_CONDITION</span></span>|<span data-ttu-id="b1354-534">String</span><span class="sxs-lookup"><span data-stu-id="b1354-534">String</span></span>|  
|<span data-ttu-id="b1354-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1354-535">INTEGRATED</span></span>|<span data-ttu-id="b1354-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="b1354-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="b1354-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="b1354-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="b1354-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b1354-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-539">Tables</span></span>  
  
-   <span data-ttu-id="b1354-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-540">Columns</span></span>  
  
-   <span data-ttu-id="b1354-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-541">Procedures</span></span>  
  
-   <span data-ttu-id="b1354-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="b1354-542">Views</span></span>  
  
-   <span data-ttu-id="b1354-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="b1354-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="b1354-544">Tables</span></span>  
  
|<span data-ttu-id="b1354-545">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-545">ColumnName</span></span>|<span data-ttu-id="b1354-546">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-547">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-548">String</span><span class="sxs-lookup"><span data-stu-id="b1354-548">String</span></span>|  
|<span data-ttu-id="b1354-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-550">String</span><span class="sxs-lookup"><span data-stu-id="b1354-550">String</span></span>|  
|<span data-ttu-id="b1354-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-551">TABLE_NAME</span></span>|<span data-ttu-id="b1354-552">String</span><span class="sxs-lookup"><span data-stu-id="b1354-552">String</span></span>|  
|<span data-ttu-id="b1354-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-553">TABLE_TYPE</span></span>|<span data-ttu-id="b1354-554">String</span><span class="sxs-lookup"><span data-stu-id="b1354-554">String</span></span>|  
|<span data-ttu-id="b1354-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-555">TABLE_GUID</span></span>|<span data-ttu-id="b1354-556">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-556">Guid</span></span>|  
|<span data-ttu-id="b1354-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-557">DESCRIPTION</span></span>|<span data-ttu-id="b1354-558">String</span><span class="sxs-lookup"><span data-stu-id="b1354-558">String</span></span>|  
|<span data-ttu-id="b1354-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-559">TABLE_PROPID</span></span>|<span data-ttu-id="b1354-560">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-560">Int64</span></span>|  
|<span data-ttu-id="b1354-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-561">DATE_CREATED</span></span>|<span data-ttu-id="b1354-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-562">DateTime</span></span>|  
|<span data-ttu-id="b1354-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-563">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b1354-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-565">Columns</span></span>  
  
|<span data-ttu-id="b1354-566">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-566">ColumnName</span></span>|<span data-ttu-id="b1354-567">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-568">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-569">String</span><span class="sxs-lookup"><span data-stu-id="b1354-569">String</span></span>|  
|<span data-ttu-id="b1354-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-571">String</span><span class="sxs-lookup"><span data-stu-id="b1354-571">String</span></span>|  
|<span data-ttu-id="b1354-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-572">TABLE_NAME</span></span>|<span data-ttu-id="b1354-573">String</span><span class="sxs-lookup"><span data-stu-id="b1354-573">String</span></span>|  
|<span data-ttu-id="b1354-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-574">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-575">String</span><span class="sxs-lookup"><span data-stu-id="b1354-575">String</span></span>|  
|<span data-ttu-id="b1354-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-576">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-577">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-577">Guid</span></span>|  
|<span data-ttu-id="b1354-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-578">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-579">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-579">Int64</span></span>|  
|<span data-ttu-id="b1354-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-581">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-581">Int64</span></span>|  
|<span data-ttu-id="b1354-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="b1354-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-583">Boolean</span></span>|  
|<span data-ttu-id="b1354-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="b1354-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="b1354-585">String</span><span class="sxs-lookup"><span data-stu-id="b1354-585">String</span></span>|  
|<span data-ttu-id="b1354-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="b1354-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="b1354-587">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-587">Int64</span></span>|  
|<span data-ttu-id="b1354-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-588">IS_NULLABLE</span></span>|<span data-ttu-id="b1354-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-589">Boolean</span></span>|  
|<span data-ttu-id="b1354-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-590">DATA_TYPE</span></span>|<span data-ttu-id="b1354-591">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-591">Int32</span></span>|  
|<span data-ttu-id="b1354-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-592">TYPE_GUID</span></span>|<span data-ttu-id="b1354-593">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-593">Guid</span></span>|  
|<span data-ttu-id="b1354-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="b1354-595">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-595">Int64</span></span>|  
|<span data-ttu-id="b1354-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b1354-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="b1354-597">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-597">Int64</span></span>|  
|<span data-ttu-id="b1354-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="b1354-599">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-599">Int32</span></span>|  
|<span data-ttu-id="b1354-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="b1354-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="b1354-601">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-601">Int16</span></span>|  
|<span data-ttu-id="b1354-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="b1354-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="b1354-603">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-603">Int64</span></span>|  
|<span data-ttu-id="b1354-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="b1354-605">String</span><span class="sxs-lookup"><span data-stu-id="b1354-605">String</span></span>|  
|<span data-ttu-id="b1354-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="b1354-607">String</span><span class="sxs-lookup"><span data-stu-id="b1354-607">String</span></span>|  
|<span data-ttu-id="b1354-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="b1354-609">String</span><span class="sxs-lookup"><span data-stu-id="b1354-609">String</span></span>|  
|<span data-ttu-id="b1354-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="b1354-611">String</span><span class="sxs-lookup"><span data-stu-id="b1354-611">String</span></span>|  
|<span data-ttu-id="b1354-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="b1354-613">String</span><span class="sxs-lookup"><span data-stu-id="b1354-613">String</span></span>|  
|<span data-ttu-id="b1354-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-614">COLLATION_NAME</span></span>|<span data-ttu-id="b1354-615">String</span><span class="sxs-lookup"><span data-stu-id="b1354-615">String</span></span>|  
|<span data-ttu-id="b1354-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="b1354-617">String</span><span class="sxs-lookup"><span data-stu-id="b1354-617">String</span></span>|  
|<span data-ttu-id="b1354-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="b1354-619">String</span><span class="sxs-lookup"><span data-stu-id="b1354-619">String</span></span>|  
|<span data-ttu-id="b1354-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-620">DOMAIN_NAME</span></span>|<span data-ttu-id="b1354-621">String</span><span class="sxs-lookup"><span data-stu-id="b1354-621">String</span></span>|  
|<span data-ttu-id="b1354-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-622">DESCRIPTION</span></span>|<span data-ttu-id="b1354-623">String</span><span class="sxs-lookup"><span data-stu-id="b1354-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b1354-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="b1354-624">Procedures</span></span>  
  
|<span data-ttu-id="b1354-625">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-625">ColumnName</span></span>|<span data-ttu-id="b1354-626">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="b1354-628">String</span><span class="sxs-lookup"><span data-stu-id="b1354-628">String</span></span>|  
|<span data-ttu-id="b1354-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="b1354-630">String</span><span class="sxs-lookup"><span data-stu-id="b1354-630">String</span></span>|  
|<span data-ttu-id="b1354-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="b1354-632">String</span><span class="sxs-lookup"><span data-stu-id="b1354-632">String</span></span>|  
|<span data-ttu-id="b1354-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b1354-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b1354-634">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-634">Int16</span></span>|  
|<span data-ttu-id="b1354-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1354-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="b1354-636">String</span><span class="sxs-lookup"><span data-stu-id="b1354-636">String</span></span>|  
|<span data-ttu-id="b1354-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-637">DESCRIPTION</span></span>|<span data-ttu-id="b1354-638">String</span><span class="sxs-lookup"><span data-stu-id="b1354-638">String</span></span>|  
|<span data-ttu-id="b1354-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-639">DATE_CREATED</span></span>|<span data-ttu-id="b1354-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-640">DateTime</span></span>|  
|<span data-ttu-id="b1354-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-641">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="b1354-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="b1354-643">Views</span></span>  
  
|<span data-ttu-id="b1354-644">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-644">ColumnName</span></span>|<span data-ttu-id="b1354-645">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-646">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-647">String</span><span class="sxs-lookup"><span data-stu-id="b1354-647">String</span></span>|  
|<span data-ttu-id="b1354-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-649">String</span><span class="sxs-lookup"><span data-stu-id="b1354-649">String</span></span>|  
|<span data-ttu-id="b1354-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-650">TABLE_NAME</span></span>|<span data-ttu-id="b1354-651">String</span><span class="sxs-lookup"><span data-stu-id="b1354-651">String</span></span>|  
|<span data-ttu-id="b1354-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="b1354-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="b1354-653">String</span><span class="sxs-lookup"><span data-stu-id="b1354-653">String</span></span>|  
|<span data-ttu-id="b1354-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="b1354-654">CHECK_OPTION</span></span>|<span data-ttu-id="b1354-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-655">Boolean</span></span>|  
|<span data-ttu-id="b1354-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="b1354-656">IS_UPDATABLE</span></span>|<span data-ttu-id="b1354-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-657">Boolean</span></span>|  
|<span data-ttu-id="b1354-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="b1354-658">DESCRIPTION</span></span>|<span data-ttu-id="b1354-659">String</span><span class="sxs-lookup"><span data-stu-id="b1354-659">String</span></span>|  
|<span data-ttu-id="b1354-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="b1354-660">DATE_CREATED</span></span>|<span data-ttu-id="b1354-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-661">DateTime</span></span>|  
|<span data-ttu-id="b1354-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="b1354-662">DATE_MODIFIED</span></span>|<span data-ttu-id="b1354-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="b1354-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b1354-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="b1354-664">Indexes</span></span>  
  
|<span data-ttu-id="b1354-665">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="b1354-665">ColumnName</span></span>|<span data-ttu-id="b1354-666">DataType</span><span class="sxs-lookup"><span data-stu-id="b1354-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b1354-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-667">TABLE_CATALOG</span></span>|<span data-ttu-id="b1354-668">String</span><span class="sxs-lookup"><span data-stu-id="b1354-668">String</span></span>|  
|<span data-ttu-id="b1354-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="b1354-670">String</span><span class="sxs-lookup"><span data-stu-id="b1354-670">String</span></span>|  
|<span data-ttu-id="b1354-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-671">TABLE_NAME</span></span>|<span data-ttu-id="b1354-672">String</span><span class="sxs-lookup"><span data-stu-id="b1354-672">String</span></span>|  
|<span data-ttu-id="b1354-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b1354-673">INDEX_CATALOG</span></span>|<span data-ttu-id="b1354-674">String</span><span class="sxs-lookup"><span data-stu-id="b1354-674">String</span></span>|  
|<span data-ttu-id="b1354-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b1354-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="b1354-676">String</span><span class="sxs-lookup"><span data-stu-id="b1354-676">String</span></span>|  
|<span data-ttu-id="b1354-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-677">INDEX_NAME</span></span>|<span data-ttu-id="b1354-678">String</span><span class="sxs-lookup"><span data-stu-id="b1354-678">String</span></span>|  
|<span data-ttu-id="b1354-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="b1354-679">PRIMARY_KEY</span></span>|<span data-ttu-id="b1354-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-680">Boolean</span></span>|  
|<span data-ttu-id="b1354-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b1354-681">UNIQUE</span></span>|<span data-ttu-id="b1354-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-682">Boolean</span></span>|  
|<span data-ttu-id="b1354-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="b1354-683">CLUSTERED</span></span>|<span data-ttu-id="b1354-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-684">Boolean</span></span>|  
|<span data-ttu-id="b1354-685">TYP</span><span class="sxs-lookup"><span data-stu-id="b1354-685">TYPE</span></span>|<span data-ttu-id="b1354-686">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-686">Int32</span></span>|  
|<span data-ttu-id="b1354-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="b1354-687">FILL_FACTOR</span></span>|<span data-ttu-id="b1354-688">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-688">Int32</span></span>|  
|<span data-ttu-id="b1354-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="b1354-689">INITIAL_SIZE</span></span>|<span data-ttu-id="b1354-690">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-690">Int32</span></span>|  
|<span data-ttu-id="b1354-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="b1354-691">NULLS</span></span>|<span data-ttu-id="b1354-692">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-692">Int32</span></span>|  
|<span data-ttu-id="b1354-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="b1354-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="b1354-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-694">Boolean</span></span>|  
|<span data-ttu-id="b1354-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="b1354-695">AUTO_UPDATE</span></span>|<span data-ttu-id="b1354-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-696">Boolean</span></span>|  
|<span data-ttu-id="b1354-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="b1354-697">NULL_COLLATION</span></span>|<span data-ttu-id="b1354-698">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-698">Int32</span></span>|  
|<span data-ttu-id="b1354-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b1354-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="b1354-700">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-700">Int64</span></span>|  
|<span data-ttu-id="b1354-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b1354-701">COLUMN_NAME</span></span>|<span data-ttu-id="b1354-702">String</span><span class="sxs-lookup"><span data-stu-id="b1354-702">String</span></span>|  
|<span data-ttu-id="b1354-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="b1354-703">COLUMN_GUID</span></span>|<span data-ttu-id="b1354-704">Guid</span><span class="sxs-lookup"><span data-stu-id="b1354-704">Guid</span></span>|  
|<span data-ttu-id="b1354-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="b1354-705">COLUMN_PROPID</span></span>|<span data-ttu-id="b1354-706">Int64</span><span class="sxs-lookup"><span data-stu-id="b1354-706">Int64</span></span>|  
|<span data-ttu-id="b1354-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="b1354-707">COLLATION</span></span>|<span data-ttu-id="b1354-708">Int16</span><span class="sxs-lookup"><span data-stu-id="b1354-708">Int16</span></span>|  
|<span data-ttu-id="b1354-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="b1354-709">CARDINALITY</span></span>|<span data-ttu-id="b1354-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="b1354-710">Decimal</span></span>|  
|<span data-ttu-id="b1354-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="b1354-711">PAGES</span></span>|<span data-ttu-id="b1354-712">Int32</span><span class="sxs-lookup"><span data-stu-id="b1354-712">Int32</span></span>|  
|<span data-ttu-id="b1354-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b1354-713">FILTER_CONDITION</span></span>|<span data-ttu-id="b1354-714">String</span><span class="sxs-lookup"><span data-stu-id="b1354-714">String</span></span>|  
|<span data-ttu-id="b1354-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="b1354-715">INTEGRATED</span></span>|<span data-ttu-id="b1354-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="b1354-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1354-717">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1354-717">See also</span></span>

- [<span data-ttu-id="b1354-718">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b1354-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
