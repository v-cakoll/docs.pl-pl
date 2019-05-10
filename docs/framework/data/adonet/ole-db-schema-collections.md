---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6c3441e86d4c5267418cf8002ba17d539c464d5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645894"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="6d93f-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="6d93f-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="6d93f-103">W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="6d93f-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="6d93f-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="6d93f-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="6d93f-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="6d93f-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="6d93f-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-106">Tables</span></span>  
  
- <span data-ttu-id="6d93f-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-107">Columns</span></span>  
  
- <span data-ttu-id="6d93f-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-108">Procedures</span></span>  
  
- <span data-ttu-id="6d93f-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d93f-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="6d93f-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="6d93f-110">Catalog</span></span>  
  
- <span data-ttu-id="6d93f-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d93f-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-112">Tables</span></span>  
  
|<span data-ttu-id="6d93f-113">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-113">ColumnName</span></span>|<span data-ttu-id="6d93f-114">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-115">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-116">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-116">String</span></span>|  
|<span data-ttu-id="6d93f-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-118">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-118">String</span></span>|  
|<span data-ttu-id="6d93f-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-119">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-120">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-120">String</span></span>|  
|<span data-ttu-id="6d93f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-121">TABLE_TYPE</span></span>|<span data-ttu-id="6d93f-122">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-122">String</span></span>|  
|<span data-ttu-id="6d93f-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-123">TABLE_GUID</span></span>|<span data-ttu-id="6d93f-124">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-124">Guid</span></span>|  
|<span data-ttu-id="6d93f-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-125">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-126">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-126">String</span></span>|  
|<span data-ttu-id="6d93f-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-127">TABLE_PROPID</span></span>|<span data-ttu-id="6d93f-128">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-128">Int64</span></span>|  
|<span data-ttu-id="6d93f-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-129">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-130">DateTime</span></span>|  
|<span data-ttu-id="6d93f-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-131">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d93f-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-133">Columns</span></span>  
  
|<span data-ttu-id="6d93f-134">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-134">ColumnName</span></span>|<span data-ttu-id="6d93f-135">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-136">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-137">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-137">String</span></span>|  
|<span data-ttu-id="6d93f-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-139">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-139">String</span></span>|  
|<span data-ttu-id="6d93f-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-140">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-141">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-141">String</span></span>|  
|<span data-ttu-id="6d93f-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-142">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-143">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-143">String</span></span>|  
|<span data-ttu-id="6d93f-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-144">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-145">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-145">Guid</span></span>|  
|<span data-ttu-id="6d93f-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-146">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-147">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-147">Int64</span></span>|  
|<span data-ttu-id="6d93f-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-149">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-149">Int64</span></span>|  
|<span data-ttu-id="6d93f-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d93f-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-151">Boolean</span></span>|  
|<span data-ttu-id="6d93f-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d93f-153">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-153">String</span></span>|  
|<span data-ttu-id="6d93f-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d93f-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d93f-155">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-155">Int64</span></span>|  
|<span data-ttu-id="6d93f-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-156">IS_NULLABLE</span></span>|<span data-ttu-id="6d93f-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-157">Boolean</span></span>|  
|<span data-ttu-id="6d93f-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-158">DATA_TYPE</span></span>|<span data-ttu-id="6d93f-159">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-159">Int32</span></span>|  
|<span data-ttu-id="6d93f-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-160">TYPE_GUID</span></span>|<span data-ttu-id="6d93f-161">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-161">Guid</span></span>|  
|<span data-ttu-id="6d93f-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d93f-163">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-163">Int64</span></span>|  
|<span data-ttu-id="6d93f-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d93f-165">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-165">Int64</span></span>|  
|<span data-ttu-id="6d93f-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d93f-167">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-167">Int32</span></span>|  
|<span data-ttu-id="6d93f-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d93f-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d93f-169">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-169">Int16</span></span>|  
|<span data-ttu-id="6d93f-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d93f-171">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-171">Int64</span></span>|  
|<span data-ttu-id="6d93f-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d93f-173">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-173">String</span></span>|  
|<span data-ttu-id="6d93f-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d93f-175">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-175">String</span></span>|  
|<span data-ttu-id="6d93f-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d93f-177">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-177">String</span></span>|  
|<span data-ttu-id="6d93f-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d93f-179">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-179">String</span></span>|  
|<span data-ttu-id="6d93f-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d93f-181">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-181">String</span></span>|  
|<span data-ttu-id="6d93f-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-182">COLLATION_NAME</span></span>|<span data-ttu-id="6d93f-183">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-183">String</span></span>|  
|<span data-ttu-id="6d93f-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d93f-185">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-185">String</span></span>|  
|<span data-ttu-id="6d93f-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d93f-187">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-187">String</span></span>|  
|<span data-ttu-id="6d93f-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-188">DOMAIN_NAME</span></span>|<span data-ttu-id="6d93f-189">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-189">String</span></span>|  
|<span data-ttu-id="6d93f-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-190">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-191">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-191">String</span></span>|  
|<span data-ttu-id="6d93f-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="6d93f-192">COLUMN_LCID</span></span>|<span data-ttu-id="6d93f-193">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-193">Int32</span></span>|  
|<span data-ttu-id="6d93f-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="6d93f-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="6d93f-195">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-195">Int32</span></span>|  
|<span data-ttu-id="6d93f-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="6d93f-196">COLUMN_SORTID</span></span>|<span data-ttu-id="6d93f-197">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-197">Int32</span></span>|  
|<span data-ttu-id="6d93f-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="6d93f-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="6d93f-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="6d93f-199">Byte[]</span></span>|  
|<span data-ttu-id="6d93f-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="6d93f-200">IS_COMPUTED</span></span>|<span data-ttu-id="6d93f-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d93f-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-202">Procedures</span></span>  
  
|<span data-ttu-id="6d93f-203">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-203">ColumnName</span></span>|<span data-ttu-id="6d93f-204">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d93f-206">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-206">String</span></span>|  
|<span data-ttu-id="6d93f-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d93f-208">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-208">String</span></span>|  
|<span data-ttu-id="6d93f-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d93f-210">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-210">String</span></span>|  
|<span data-ttu-id="6d93f-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d93f-212">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-212">Int16</span></span>|  
|<span data-ttu-id="6d93f-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d93f-214">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-214">String</span></span>|  
|<span data-ttu-id="6d93f-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-215">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-216">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-216">String</span></span>|  
|<span data-ttu-id="6d93f-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-217">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-218">DateTime</span></span>|  
|<span data-ttu-id="6d93f-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-219">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="6d93f-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d93f-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="6d93f-222">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-222">ColumnName</span></span>|<span data-ttu-id="6d93f-223">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d93f-225">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-225">String</span></span>|  
|<span data-ttu-id="6d93f-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d93f-227">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-227">String</span></span>|  
|<span data-ttu-id="6d93f-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d93f-229">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-229">String</span></span>|  
|<span data-ttu-id="6d93f-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-230">PARAMETER_NAME</span></span>|<span data-ttu-id="6d93f-231">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-231">String</span></span>|  
|<span data-ttu-id="6d93f-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-233">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-233">Int32</span></span>|  
|<span data-ttu-id="6d93f-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="6d93f-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="6d93f-235">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-235">Int32</span></span>|  
|<span data-ttu-id="6d93f-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="6d93f-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-237">Boolean</span></span>|  
|<span data-ttu-id="6d93f-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="6d93f-239">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-239">String</span></span>|  
|<span data-ttu-id="6d93f-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-240">IS_NULLABLE</span></span>|<span data-ttu-id="6d93f-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-241">Boolean</span></span>|  
|<span data-ttu-id="6d93f-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-242">DATA_TYPE</span></span>|<span data-ttu-id="6d93f-243">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-243">Int32</span></span>|  
|<span data-ttu-id="6d93f-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d93f-245">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-245">Int64</span></span>|  
|<span data-ttu-id="6d93f-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d93f-247">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-247">Int64</span></span>|  
|<span data-ttu-id="6d93f-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d93f-249">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-249">Int32</span></span>|  
|<span data-ttu-id="6d93f-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d93f-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d93f-251">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-251">Int16</span></span>|  
|<span data-ttu-id="6d93f-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-252">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-253">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-253">String</span></span>|  
|<span data-ttu-id="6d93f-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-254">TYPE_NAME</span></span>|<span data-ttu-id="6d93f-255">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-255">String</span></span>|  
|<span data-ttu-id="6d93f-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="6d93f-257">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="6d93f-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="6d93f-258">Catalog</span></span>  
  
|<span data-ttu-id="6d93f-259">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-259">ColumnName</span></span>|<span data-ttu-id="6d93f-260">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-261">CATALOG_NAME</span></span>|<span data-ttu-id="6d93f-262">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-262">String</span></span>|  
|<span data-ttu-id="6d93f-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-263">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-264">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d93f-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-265">Indexes</span></span>  
  
|<span data-ttu-id="6d93f-266">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-266">ColumnName</span></span>|<span data-ttu-id="6d93f-267">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-268">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-269">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-269">String</span></span>|  
|<span data-ttu-id="6d93f-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-271">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-271">String</span></span>|  
|<span data-ttu-id="6d93f-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-272">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-273">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-273">String</span></span>|  
|<span data-ttu-id="6d93f-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-274">INDEX_CATALOG</span></span>|<span data-ttu-id="6d93f-275">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-275">String</span></span>|  
|<span data-ttu-id="6d93f-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d93f-277">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-277">String</span></span>|  
|<span data-ttu-id="6d93f-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-278">INDEX_NAME</span></span>|<span data-ttu-id="6d93f-279">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-279">String</span></span>|  
|<span data-ttu-id="6d93f-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d93f-280">PRIMARY_KEY</span></span>|<span data-ttu-id="6d93f-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-281">Boolean</span></span>|  
|<span data-ttu-id="6d93f-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6d93f-282">UNIQUE</span></span>|<span data-ttu-id="6d93f-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-283">Boolean</span></span>|  
|<span data-ttu-id="6d93f-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d93f-284">CLUSTERED</span></span>|<span data-ttu-id="6d93f-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-285">Boolean</span></span>|  
|<span data-ttu-id="6d93f-286">TYP</span><span class="sxs-lookup"><span data-stu-id="6d93f-286">TYPE</span></span>|<span data-ttu-id="6d93f-287">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-287">Int32</span></span>|  
|<span data-ttu-id="6d93f-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d93f-288">FILL_FACTOR</span></span>|<span data-ttu-id="6d93f-289">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-289">Int32</span></span>|  
|<span data-ttu-id="6d93f-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d93f-290">INITIAL_SIZE</span></span>|<span data-ttu-id="6d93f-291">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-291">Int32</span></span>|  
|<span data-ttu-id="6d93f-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="6d93f-292">NULLS</span></span>|<span data-ttu-id="6d93f-293">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-293">Int32</span></span>|  
|<span data-ttu-id="6d93f-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d93f-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d93f-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-295">Boolean</span></span>|  
|<span data-ttu-id="6d93f-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d93f-296">AUTO_UPDATE</span></span>|<span data-ttu-id="6d93f-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-297">Boolean</span></span>|  
|<span data-ttu-id="6d93f-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d93f-298">NULL_COLLATION</span></span>|<span data-ttu-id="6d93f-299">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-299">Int32</span></span>|  
|<span data-ttu-id="6d93f-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-301">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-301">Int64</span></span>|  
|<span data-ttu-id="6d93f-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-302">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-303">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-303">String</span></span>|  
|<span data-ttu-id="6d93f-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-304">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-305">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-305">Guid</span></span>|  
|<span data-ttu-id="6d93f-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-306">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-307">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-307">Int64</span></span>|  
|<span data-ttu-id="6d93f-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="6d93f-308">COLLATION</span></span>|<span data-ttu-id="6d93f-309">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-309">Int16</span></span>|  
|<span data-ttu-id="6d93f-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="6d93f-310">CARDINALITY</span></span>|<span data-ttu-id="6d93f-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="6d93f-311">Decimal</span></span>|  
|<span data-ttu-id="6d93f-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="6d93f-312">PAGES</span></span>|<span data-ttu-id="6d93f-313">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-313">Int32</span></span>|  
|<span data-ttu-id="6d93f-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-314">FILTER_CONDITION</span></span>|<span data-ttu-id="6d93f-315">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-315">String</span></span>|  
|<span data-ttu-id="6d93f-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-316">INTEGRATED</span></span>|<span data-ttu-id="6d93f-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="6d93f-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="6d93f-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="6d93f-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="6d93f-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="6d93f-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-320">Tables</span></span>  
  
- <span data-ttu-id="6d93f-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-321">Columns</span></span>  
  
- <span data-ttu-id="6d93f-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-322">Procedures</span></span>  
  
- <span data-ttu-id="6d93f-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6d93f-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="6d93f-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6d93f-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="6d93f-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="6d93f-325">Views</span></span>  
  
- <span data-ttu-id="6d93f-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d93f-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-327">Tables</span></span>  
  
|<span data-ttu-id="6d93f-328">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-328">ColumnName</span></span>|<span data-ttu-id="6d93f-329">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-330">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-331">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-331">String</span></span>|  
|<span data-ttu-id="6d93f-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-333">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-333">String</span></span>|  
|<span data-ttu-id="6d93f-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-334">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-335">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-335">String</span></span>|  
|<span data-ttu-id="6d93f-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-336">TABLE_TYPE</span></span>|<span data-ttu-id="6d93f-337">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-337">String</span></span>|  
|<span data-ttu-id="6d93f-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-338">TABLE_GUID</span></span>|<span data-ttu-id="6d93f-339">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-339">Guid</span></span>|  
|<span data-ttu-id="6d93f-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-340">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-341">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-341">String</span></span>|  
|<span data-ttu-id="6d93f-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-342">TABLE_PROPID</span></span>|<span data-ttu-id="6d93f-343">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-343">Int64</span></span>|  
|<span data-ttu-id="6d93f-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-344">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-345">DateTime</span></span>|  
|<span data-ttu-id="6d93f-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-346">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d93f-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-348">Columns</span></span>  
  
|<span data-ttu-id="6d93f-349">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-349">ColumnName</span></span>|<span data-ttu-id="6d93f-350">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-351">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-352">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-352">String</span></span>|  
|<span data-ttu-id="6d93f-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-354">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-354">String</span></span>|  
|<span data-ttu-id="6d93f-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-355">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-356">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-356">String</span></span>|  
|<span data-ttu-id="6d93f-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-357">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-358">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-358">String</span></span>|  
|<span data-ttu-id="6d93f-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-359">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-360">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-360">Guid</span></span>|  
|<span data-ttu-id="6d93f-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-361">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-362">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-362">Int64</span></span>|  
|<span data-ttu-id="6d93f-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-364">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-364">Int64</span></span>|  
|<span data-ttu-id="6d93f-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d93f-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-366">Boolean</span></span>|  
|<span data-ttu-id="6d93f-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d93f-368">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-368">String</span></span>|  
|<span data-ttu-id="6d93f-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d93f-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d93f-370">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-370">Int64</span></span>|  
|<span data-ttu-id="6d93f-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-371">IS_NULLABLE</span></span>|<span data-ttu-id="6d93f-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-372">Boolean</span></span>|  
|<span data-ttu-id="6d93f-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-373">DATA_TYPE</span></span>|<span data-ttu-id="6d93f-374">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-374">Int32</span></span>|  
|<span data-ttu-id="6d93f-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-375">TYPE_GUID</span></span>|<span data-ttu-id="6d93f-376">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-376">Guid</span></span>|  
|<span data-ttu-id="6d93f-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d93f-378">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-378">Int64</span></span>|  
|<span data-ttu-id="6d93f-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d93f-380">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-380">Int64</span></span>|  
|<span data-ttu-id="6d93f-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d93f-382">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-382">Int32</span></span>|  
|<span data-ttu-id="6d93f-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d93f-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d93f-384">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-384">Int16</span></span>|  
|<span data-ttu-id="6d93f-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d93f-386">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-386">Int64</span></span>|  
|<span data-ttu-id="6d93f-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d93f-388">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-388">String</span></span>|  
|<span data-ttu-id="6d93f-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d93f-390">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-390">String</span></span>|  
|<span data-ttu-id="6d93f-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d93f-392">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-392">String</span></span>|  
|<span data-ttu-id="6d93f-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d93f-394">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-394">String</span></span>|  
|<span data-ttu-id="6d93f-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d93f-396">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-396">String</span></span>|  
|<span data-ttu-id="6d93f-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-397">COLLATION_NAME</span></span>|<span data-ttu-id="6d93f-398">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-398">String</span></span>|  
|<span data-ttu-id="6d93f-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d93f-400">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-400">String</span></span>|  
|<span data-ttu-id="6d93f-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d93f-402">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-402">String</span></span>|  
|<span data-ttu-id="6d93f-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-403">DOMAIN_NAME</span></span>|<span data-ttu-id="6d93f-404">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-404">String</span></span>|  
|<span data-ttu-id="6d93f-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-405">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-406">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d93f-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-407">Procedures</span></span>  
  
|<span data-ttu-id="6d93f-408">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-408">ColumnName</span></span>|<span data-ttu-id="6d93f-409">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d93f-411">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-411">String</span></span>|  
|<span data-ttu-id="6d93f-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d93f-413">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-413">String</span></span>|  
|<span data-ttu-id="6d93f-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d93f-415">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-415">String</span></span>|  
|<span data-ttu-id="6d93f-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d93f-417">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-417">Int16</span></span>|  
|<span data-ttu-id="6d93f-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d93f-419">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-419">String</span></span>|  
|<span data-ttu-id="6d93f-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-420">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-421">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-421">String</span></span>|  
|<span data-ttu-id="6d93f-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-422">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-423">DateTime</span></span>|  
|<span data-ttu-id="6d93f-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-424">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="6d93f-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6d93f-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="6d93f-427">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-427">ColumnName</span></span>|<span data-ttu-id="6d93f-428">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d93f-430">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-430">String</span></span>|  
|<span data-ttu-id="6d93f-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d93f-432">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-432">String</span></span>|  
|<span data-ttu-id="6d93f-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d93f-434">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-434">String</span></span>|  
|<span data-ttu-id="6d93f-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-435">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-436">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-436">String</span></span>|  
|<span data-ttu-id="6d93f-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-437">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-438">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-438">Guid</span></span>|  
|<span data-ttu-id="6d93f-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-439">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-440">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-440">Int64</span></span>|  
|<span data-ttu-id="6d93f-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="6d93f-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="6d93f-442">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-442">Int64</span></span>|  
|<span data-ttu-id="6d93f-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-444">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-444">Int64</span></span>|  
|<span data-ttu-id="6d93f-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-445">IS_NULLABLE</span></span>|<span data-ttu-id="6d93f-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-446">Boolean</span></span>|  
|<span data-ttu-id="6d93f-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-447">DATA_TYPE</span></span>|<span data-ttu-id="6d93f-448">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-448">Int32</span></span>|  
|<span data-ttu-id="6d93f-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-449">TYPE_GUID</span></span>|<span data-ttu-id="6d93f-450">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-450">Guid</span></span>|  
|<span data-ttu-id="6d93f-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d93f-452">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-452">Int64</span></span>|  
|<span data-ttu-id="6d93f-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d93f-454">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-454">Int64</span></span>|  
|<span data-ttu-id="6d93f-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d93f-456">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-456">Int32</span></span>|  
|<span data-ttu-id="6d93f-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d93f-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d93f-458">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-458">Int16</span></span>|  
|<span data-ttu-id="6d93f-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-459">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-460">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-460">String</span></span>|  
|<span data-ttu-id="6d93f-461">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="6d93f-461">OVERLOAD</span></span>|<span data-ttu-id="6d93f-462">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6d93f-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="6d93f-463">Views</span></span>  
  
|<span data-ttu-id="6d93f-464">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-464">ColumnName</span></span>|<span data-ttu-id="6d93f-465">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-466">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-467">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-467">String</span></span>|  
|<span data-ttu-id="6d93f-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-469">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-469">String</span></span>|  
|<span data-ttu-id="6d93f-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-470">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-471">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-471">String</span></span>|  
|<span data-ttu-id="6d93f-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="6d93f-473">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-473">String</span></span>|  
|<span data-ttu-id="6d93f-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6d93f-474">CHECK_OPTION</span></span>|<span data-ttu-id="6d93f-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-475">Boolean</span></span>|  
|<span data-ttu-id="6d93f-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-476">IS_UPDATABLE</span></span>|<span data-ttu-id="6d93f-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-477">Boolean</span></span>|  
|<span data-ttu-id="6d93f-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-478">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-479">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-479">String</span></span>|  
|<span data-ttu-id="6d93f-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-480">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-481">DateTime</span></span>|  
|<span data-ttu-id="6d93f-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-482">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d93f-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-484">Indexes</span></span>  
  
|<span data-ttu-id="6d93f-485">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-485">ColumnName</span></span>|<span data-ttu-id="6d93f-486">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-487">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-488">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-488">String</span></span>|  
|<span data-ttu-id="6d93f-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-490">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-490">String</span></span>|  
|<span data-ttu-id="6d93f-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-491">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-492">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-492">String</span></span>|  
|<span data-ttu-id="6d93f-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-493">INDEX_CATALOG</span></span>|<span data-ttu-id="6d93f-494">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-494">String</span></span>|  
|<span data-ttu-id="6d93f-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d93f-496">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-496">String</span></span>|  
|<span data-ttu-id="6d93f-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-497">INDEX_NAME</span></span>|<span data-ttu-id="6d93f-498">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-498">String</span></span>|  
|<span data-ttu-id="6d93f-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d93f-499">PRIMARY_KEY</span></span>|<span data-ttu-id="6d93f-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-500">Boolean</span></span>|  
|<span data-ttu-id="6d93f-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6d93f-501">UNIQUE</span></span>|<span data-ttu-id="6d93f-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-502">Boolean</span></span>|  
|<span data-ttu-id="6d93f-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d93f-503">CLUSTERED</span></span>|<span data-ttu-id="6d93f-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-504">Boolean</span></span>|  
|<span data-ttu-id="6d93f-505">TYP</span><span class="sxs-lookup"><span data-stu-id="6d93f-505">TYPE</span></span>|<span data-ttu-id="6d93f-506">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-506">Int32</span></span>|  
|<span data-ttu-id="6d93f-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d93f-507">FILL_FACTOR</span></span>|<span data-ttu-id="6d93f-508">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-508">Int32</span></span>|  
|<span data-ttu-id="6d93f-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d93f-509">INITIAL_SIZE</span></span>|<span data-ttu-id="6d93f-510">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-510">Int32</span></span>|  
|<span data-ttu-id="6d93f-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="6d93f-511">NULLS</span></span>|<span data-ttu-id="6d93f-512">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-512">Int32</span></span>|  
|<span data-ttu-id="6d93f-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d93f-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d93f-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-514">Boolean</span></span>|  
|<span data-ttu-id="6d93f-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d93f-515">AUTO_UPDATE</span></span>|<span data-ttu-id="6d93f-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-516">Boolean</span></span>|  
|<span data-ttu-id="6d93f-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d93f-517">NULL_COLLATION</span></span>|<span data-ttu-id="6d93f-518">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-518">Int32</span></span>|  
|<span data-ttu-id="6d93f-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-520">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-520">Int64</span></span>|  
|<span data-ttu-id="6d93f-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-521">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-522">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-522">String</span></span>|  
|<span data-ttu-id="6d93f-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-523">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-524">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-524">Guid</span></span>|  
|<span data-ttu-id="6d93f-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-525">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-526">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-526">Int64</span></span>|  
|<span data-ttu-id="6d93f-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="6d93f-527">COLLATION</span></span>|<span data-ttu-id="6d93f-528">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-528">Int16</span></span>|  
|<span data-ttu-id="6d93f-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="6d93f-529">CARDINALITY</span></span>|<span data-ttu-id="6d93f-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="6d93f-530">Decimal</span></span>|  
|<span data-ttu-id="6d93f-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="6d93f-531">PAGES</span></span>|<span data-ttu-id="6d93f-532">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-532">Int32</span></span>|  
|<span data-ttu-id="6d93f-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-533">FILTER_CONDITION</span></span>|<span data-ttu-id="6d93f-534">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-534">String</span></span>|  
|<span data-ttu-id="6d93f-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-535">INTEGRATED</span></span>|<span data-ttu-id="6d93f-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="6d93f-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="6d93f-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="6d93f-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="6d93f-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="6d93f-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-539">Tables</span></span>  
  
- <span data-ttu-id="6d93f-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-540">Columns</span></span>  
  
- <span data-ttu-id="6d93f-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-541">Procedures</span></span>  
  
- <span data-ttu-id="6d93f-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="6d93f-542">Views</span></span>  
  
- <span data-ttu-id="6d93f-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6d93f-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="6d93f-544">Tables</span></span>  
  
|<span data-ttu-id="6d93f-545">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-545">ColumnName</span></span>|<span data-ttu-id="6d93f-546">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-547">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-548">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-548">String</span></span>|  
|<span data-ttu-id="6d93f-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-550">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-550">String</span></span>|  
|<span data-ttu-id="6d93f-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-551">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-552">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-552">String</span></span>|  
|<span data-ttu-id="6d93f-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-553">TABLE_TYPE</span></span>|<span data-ttu-id="6d93f-554">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-554">String</span></span>|  
|<span data-ttu-id="6d93f-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-555">TABLE_GUID</span></span>|<span data-ttu-id="6d93f-556">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-556">Guid</span></span>|  
|<span data-ttu-id="6d93f-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-557">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-558">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-558">String</span></span>|  
|<span data-ttu-id="6d93f-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-559">TABLE_PROPID</span></span>|<span data-ttu-id="6d93f-560">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-560">Int64</span></span>|  
|<span data-ttu-id="6d93f-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-561">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-562">DateTime</span></span>|  
|<span data-ttu-id="6d93f-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-563">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6d93f-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-565">Columns</span></span>  
  
|<span data-ttu-id="6d93f-566">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-566">ColumnName</span></span>|<span data-ttu-id="6d93f-567">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-568">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-569">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-569">String</span></span>|  
|<span data-ttu-id="6d93f-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-571">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-571">String</span></span>|  
|<span data-ttu-id="6d93f-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-572">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-573">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-573">String</span></span>|  
|<span data-ttu-id="6d93f-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-574">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-575">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-575">String</span></span>|  
|<span data-ttu-id="6d93f-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-576">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-577">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-577">Guid</span></span>|  
|<span data-ttu-id="6d93f-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-578">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-579">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-579">Int64</span></span>|  
|<span data-ttu-id="6d93f-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-581">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-581">Int64</span></span>|  
|<span data-ttu-id="6d93f-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6d93f-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-583">Boolean</span></span>|  
|<span data-ttu-id="6d93f-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6d93f-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6d93f-585">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-585">String</span></span>|  
|<span data-ttu-id="6d93f-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6d93f-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="6d93f-587">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-587">Int64</span></span>|  
|<span data-ttu-id="6d93f-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-588">IS_NULLABLE</span></span>|<span data-ttu-id="6d93f-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-589">Boolean</span></span>|  
|<span data-ttu-id="6d93f-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-590">DATA_TYPE</span></span>|<span data-ttu-id="6d93f-591">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-591">Int32</span></span>|  
|<span data-ttu-id="6d93f-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-592">TYPE_GUID</span></span>|<span data-ttu-id="6d93f-593">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-593">Guid</span></span>|  
|<span data-ttu-id="6d93f-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6d93f-595">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-595">Int64</span></span>|  
|<span data-ttu-id="6d93f-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6d93f-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6d93f-597">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-597">Int64</span></span>|  
|<span data-ttu-id="6d93f-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6d93f-599">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-599">Int32</span></span>|  
|<span data-ttu-id="6d93f-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6d93f-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="6d93f-601">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-601">Int16</span></span>|  
|<span data-ttu-id="6d93f-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6d93f-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="6d93f-603">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-603">Int64</span></span>|  
|<span data-ttu-id="6d93f-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6d93f-605">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-605">String</span></span>|  
|<span data-ttu-id="6d93f-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6d93f-607">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-607">String</span></span>|  
|<span data-ttu-id="6d93f-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6d93f-609">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-609">String</span></span>|  
|<span data-ttu-id="6d93f-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="6d93f-611">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-611">String</span></span>|  
|<span data-ttu-id="6d93f-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6d93f-613">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-613">String</span></span>|  
|<span data-ttu-id="6d93f-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-614">COLLATION_NAME</span></span>|<span data-ttu-id="6d93f-615">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-615">String</span></span>|  
|<span data-ttu-id="6d93f-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6d93f-617">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-617">String</span></span>|  
|<span data-ttu-id="6d93f-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6d93f-619">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-619">String</span></span>|  
|<span data-ttu-id="6d93f-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-620">DOMAIN_NAME</span></span>|<span data-ttu-id="6d93f-621">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-621">String</span></span>|  
|<span data-ttu-id="6d93f-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-622">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-623">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6d93f-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d93f-624">Procedures</span></span>  
  
|<span data-ttu-id="6d93f-625">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-625">ColumnName</span></span>|<span data-ttu-id="6d93f-626">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6d93f-628">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-628">String</span></span>|  
|<span data-ttu-id="6d93f-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6d93f-630">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-630">String</span></span>|  
|<span data-ttu-id="6d93f-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="6d93f-632">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-632">String</span></span>|  
|<span data-ttu-id="6d93f-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6d93f-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6d93f-634">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-634">Int16</span></span>|  
|<span data-ttu-id="6d93f-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6d93f-636">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-636">String</span></span>|  
|<span data-ttu-id="6d93f-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-637">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-638">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-638">String</span></span>|  
|<span data-ttu-id="6d93f-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-639">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-640">DateTime</span></span>|  
|<span data-ttu-id="6d93f-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-641">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6d93f-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="6d93f-643">Views</span></span>  
  
|<span data-ttu-id="6d93f-644">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-644">ColumnName</span></span>|<span data-ttu-id="6d93f-645">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-646">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-647">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-647">String</span></span>|  
|<span data-ttu-id="6d93f-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-649">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-649">String</span></span>|  
|<span data-ttu-id="6d93f-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-650">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-651">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-651">String</span></span>|  
|<span data-ttu-id="6d93f-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="6d93f-653">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-653">String</span></span>|  
|<span data-ttu-id="6d93f-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6d93f-654">CHECK_OPTION</span></span>|<span data-ttu-id="6d93f-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-655">Boolean</span></span>|  
|<span data-ttu-id="6d93f-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6d93f-656">IS_UPDATABLE</span></span>|<span data-ttu-id="6d93f-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-657">Boolean</span></span>|  
|<span data-ttu-id="6d93f-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="6d93f-658">DESCRIPTION</span></span>|<span data-ttu-id="6d93f-659">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-659">String</span></span>|  
|<span data-ttu-id="6d93f-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-660">DATE_CREATED</span></span>|<span data-ttu-id="6d93f-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-661">DateTime</span></span>|  
|<span data-ttu-id="6d93f-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6d93f-662">DATE_MODIFIED</span></span>|<span data-ttu-id="6d93f-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="6d93f-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6d93f-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="6d93f-664">Indexes</span></span>  
  
|<span data-ttu-id="6d93f-665">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="6d93f-665">ColumnName</span></span>|<span data-ttu-id="6d93f-666">DataType</span><span class="sxs-lookup"><span data-stu-id="6d93f-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6d93f-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-667">TABLE_CATALOG</span></span>|<span data-ttu-id="6d93f-668">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-668">String</span></span>|  
|<span data-ttu-id="6d93f-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="6d93f-670">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-670">String</span></span>|  
|<span data-ttu-id="6d93f-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-671">TABLE_NAME</span></span>|<span data-ttu-id="6d93f-672">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-672">String</span></span>|  
|<span data-ttu-id="6d93f-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6d93f-673">INDEX_CATALOG</span></span>|<span data-ttu-id="6d93f-674">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-674">String</span></span>|  
|<span data-ttu-id="6d93f-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6d93f-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="6d93f-676">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-676">String</span></span>|  
|<span data-ttu-id="6d93f-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-677">INDEX_NAME</span></span>|<span data-ttu-id="6d93f-678">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-678">String</span></span>|  
|<span data-ttu-id="6d93f-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6d93f-679">PRIMARY_KEY</span></span>|<span data-ttu-id="6d93f-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-680">Boolean</span></span>|  
|<span data-ttu-id="6d93f-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6d93f-681">UNIQUE</span></span>|<span data-ttu-id="6d93f-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-682">Boolean</span></span>|  
|<span data-ttu-id="6d93f-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6d93f-683">CLUSTERED</span></span>|<span data-ttu-id="6d93f-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-684">Boolean</span></span>|  
|<span data-ttu-id="6d93f-685">TYP</span><span class="sxs-lookup"><span data-stu-id="6d93f-685">TYPE</span></span>|<span data-ttu-id="6d93f-686">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-686">Int32</span></span>|  
|<span data-ttu-id="6d93f-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6d93f-687">FILL_FACTOR</span></span>|<span data-ttu-id="6d93f-688">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-688">Int32</span></span>|  
|<span data-ttu-id="6d93f-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6d93f-689">INITIAL_SIZE</span></span>|<span data-ttu-id="6d93f-690">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-690">Int32</span></span>|  
|<span data-ttu-id="6d93f-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="6d93f-691">NULLS</span></span>|<span data-ttu-id="6d93f-692">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-692">Int32</span></span>|  
|<span data-ttu-id="6d93f-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6d93f-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6d93f-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-694">Boolean</span></span>|  
|<span data-ttu-id="6d93f-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6d93f-695">AUTO_UPDATE</span></span>|<span data-ttu-id="6d93f-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-696">Boolean</span></span>|  
|<span data-ttu-id="6d93f-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6d93f-697">NULL_COLLATION</span></span>|<span data-ttu-id="6d93f-698">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-698">Int32</span></span>|  
|<span data-ttu-id="6d93f-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="6d93f-700">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-700">Int64</span></span>|  
|<span data-ttu-id="6d93f-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6d93f-701">COLUMN_NAME</span></span>|<span data-ttu-id="6d93f-702">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-702">String</span></span>|  
|<span data-ttu-id="6d93f-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6d93f-703">COLUMN_GUID</span></span>|<span data-ttu-id="6d93f-704">Guid</span><span class="sxs-lookup"><span data-stu-id="6d93f-704">Guid</span></span>|  
|<span data-ttu-id="6d93f-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6d93f-705">COLUMN_PROPID</span></span>|<span data-ttu-id="6d93f-706">Int64</span><span class="sxs-lookup"><span data-stu-id="6d93f-706">Int64</span></span>|  
|<span data-ttu-id="6d93f-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="6d93f-707">COLLATION</span></span>|<span data-ttu-id="6d93f-708">Int16</span><span class="sxs-lookup"><span data-stu-id="6d93f-708">Int16</span></span>|  
|<span data-ttu-id="6d93f-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="6d93f-709">CARDINALITY</span></span>|<span data-ttu-id="6d93f-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="6d93f-710">Decimal</span></span>|  
|<span data-ttu-id="6d93f-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="6d93f-711">PAGES</span></span>|<span data-ttu-id="6d93f-712">Int32</span><span class="sxs-lookup"><span data-stu-id="6d93f-712">Int32</span></span>|  
|<span data-ttu-id="6d93f-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6d93f-713">FILTER_CONDITION</span></span>|<span data-ttu-id="6d93f-714">String</span><span class="sxs-lookup"><span data-stu-id="6d93f-714">String</span></span>|  
|<span data-ttu-id="6d93f-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="6d93f-715">INTEGRATED</span></span>|<span data-ttu-id="6d93f-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="6d93f-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d93f-717">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d93f-717">See also</span></span>

- [<span data-ttu-id="6d93f-718">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6d93f-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
