---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f753f35aab0a0200da5de463a73abb9813253d11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658458"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="2aadb-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="2aadb-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="2aadb-103">W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="2aadb-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="2aadb-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="2aadb-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="2aadb-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2aadb-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2aadb-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-106">Tables</span></span>  
  
-   <span data-ttu-id="2aadb-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-107">Columns</span></span>  
  
-   <span data-ttu-id="2aadb-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-108">Procedures</span></span>  
  
-   <span data-ttu-id="2aadb-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2aadb-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2aadb-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="2aadb-110">Catalog</span></span>  
  
-   <span data-ttu-id="2aadb-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2aadb-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-112">Tables</span></span>  
  
|<span data-ttu-id="2aadb-113">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-113">ColumnName</span></span>|<span data-ttu-id="2aadb-114">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-115">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-116">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-116">String</span></span>|  
|<span data-ttu-id="2aadb-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-118">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-118">String</span></span>|  
|<span data-ttu-id="2aadb-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-119">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-120">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-120">String</span></span>|  
|<span data-ttu-id="2aadb-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-121">TABLE_TYPE</span></span>|<span data-ttu-id="2aadb-122">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-122">String</span></span>|  
|<span data-ttu-id="2aadb-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-123">TABLE_GUID</span></span>|<span data-ttu-id="2aadb-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-124">Guid</span></span>|  
|<span data-ttu-id="2aadb-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-125">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-126">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-126">String</span></span>|  
|<span data-ttu-id="2aadb-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-127">TABLE_PROPID</span></span>|<span data-ttu-id="2aadb-128">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-128">Int64</span></span>|  
|<span data-ttu-id="2aadb-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-129">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-130">DateTime</span></span>|  
|<span data-ttu-id="2aadb-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-131">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2aadb-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-133">Columns</span></span>  
  
|<span data-ttu-id="2aadb-134">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-134">ColumnName</span></span>|<span data-ttu-id="2aadb-135">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-136">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-137">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-137">String</span></span>|  
|<span data-ttu-id="2aadb-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-139">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-139">String</span></span>|  
|<span data-ttu-id="2aadb-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-140">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-141">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-141">String</span></span>|  
|<span data-ttu-id="2aadb-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-142">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-143">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-143">String</span></span>|  
|<span data-ttu-id="2aadb-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-144">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-145">Guid</span></span>|  
|<span data-ttu-id="2aadb-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-146">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-147">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-147">Int64</span></span>|  
|<span data-ttu-id="2aadb-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-149">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-149">Int64</span></span>|  
|<span data-ttu-id="2aadb-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2aadb-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-151">Boolean</span></span>|  
|<span data-ttu-id="2aadb-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2aadb-153">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-153">String</span></span>|  
|<span data-ttu-id="2aadb-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2aadb-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="2aadb-155">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-155">Int64</span></span>|  
|<span data-ttu-id="2aadb-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-156">IS_NULLABLE</span></span>|<span data-ttu-id="2aadb-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-157">Boolean</span></span>|  
|<span data-ttu-id="2aadb-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-158">DATA_TYPE</span></span>|<span data-ttu-id="2aadb-159">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-159">Int32</span></span>|  
|<span data-ttu-id="2aadb-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-160">TYPE_GUID</span></span>|<span data-ttu-id="2aadb-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-161">Guid</span></span>|  
|<span data-ttu-id="2aadb-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2aadb-163">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-163">Int64</span></span>|  
|<span data-ttu-id="2aadb-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2aadb-165">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-165">Int64</span></span>|  
|<span data-ttu-id="2aadb-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2aadb-167">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-167">Int32</span></span>|  
|<span data-ttu-id="2aadb-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2aadb-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="2aadb-169">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-169">Int16</span></span>|  
|<span data-ttu-id="2aadb-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="2aadb-171">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-171">Int64</span></span>|  
|<span data-ttu-id="2aadb-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2aadb-173">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-173">String</span></span>|  
|<span data-ttu-id="2aadb-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2aadb-175">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-175">String</span></span>|  
|<span data-ttu-id="2aadb-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2aadb-177">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-177">String</span></span>|  
|<span data-ttu-id="2aadb-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="2aadb-179">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-179">String</span></span>|  
|<span data-ttu-id="2aadb-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2aadb-181">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-181">String</span></span>|  
|<span data-ttu-id="2aadb-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-182">COLLATION_NAME</span></span>|<span data-ttu-id="2aadb-183">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-183">String</span></span>|  
|<span data-ttu-id="2aadb-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2aadb-185">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-185">String</span></span>|  
|<span data-ttu-id="2aadb-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2aadb-187">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-187">String</span></span>|  
|<span data-ttu-id="2aadb-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-188">DOMAIN_NAME</span></span>|<span data-ttu-id="2aadb-189">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-189">String</span></span>|  
|<span data-ttu-id="2aadb-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-190">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-191">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-191">String</span></span>|  
|<span data-ttu-id="2aadb-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="2aadb-192">COLUMN_LCID</span></span>|<span data-ttu-id="2aadb-193">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-193">Int32</span></span>|  
|<span data-ttu-id="2aadb-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="2aadb-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="2aadb-195">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-195">Int32</span></span>|  
|<span data-ttu-id="2aadb-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="2aadb-196">COLUMN_SORTID</span></span>|<span data-ttu-id="2aadb-197">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-197">Int32</span></span>|  
|<span data-ttu-id="2aadb-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="2aadb-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="2aadb-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="2aadb-199">Byte[]</span></span>|  
|<span data-ttu-id="2aadb-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="2aadb-200">IS_COMPUTED</span></span>|<span data-ttu-id="2aadb-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2aadb-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-202">Procedures</span></span>  
  
|<span data-ttu-id="2aadb-203">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-203">ColumnName</span></span>|<span data-ttu-id="2aadb-204">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2aadb-206">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-206">String</span></span>|  
|<span data-ttu-id="2aadb-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2aadb-208">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-208">String</span></span>|  
|<span data-ttu-id="2aadb-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="2aadb-210">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-210">String</span></span>|  
|<span data-ttu-id="2aadb-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2aadb-212">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-212">Int16</span></span>|  
|<span data-ttu-id="2aadb-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2aadb-214">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-214">String</span></span>|  
|<span data-ttu-id="2aadb-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-215">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-216">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-216">String</span></span>|  
|<span data-ttu-id="2aadb-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-217">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-218">DateTime</span></span>|  
|<span data-ttu-id="2aadb-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-219">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="2aadb-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2aadb-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="2aadb-222">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-222">ColumnName</span></span>|<span data-ttu-id="2aadb-223">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2aadb-225">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-225">String</span></span>|  
|<span data-ttu-id="2aadb-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2aadb-227">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-227">String</span></span>|  
|<span data-ttu-id="2aadb-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="2aadb-229">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-229">String</span></span>|  
|<span data-ttu-id="2aadb-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-230">PARAMETER_NAME</span></span>|<span data-ttu-id="2aadb-231">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-231">String</span></span>|  
|<span data-ttu-id="2aadb-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-233">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-233">Int32</span></span>|  
|<span data-ttu-id="2aadb-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="2aadb-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="2aadb-235">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-235">Int32</span></span>|  
|<span data-ttu-id="2aadb-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="2aadb-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-237">Boolean</span></span>|  
|<span data-ttu-id="2aadb-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="2aadb-239">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-239">String</span></span>|  
|<span data-ttu-id="2aadb-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-240">IS_NULLABLE</span></span>|<span data-ttu-id="2aadb-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-241">Boolean</span></span>|  
|<span data-ttu-id="2aadb-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-242">DATA_TYPE</span></span>|<span data-ttu-id="2aadb-243">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-243">Int32</span></span>|  
|<span data-ttu-id="2aadb-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2aadb-245">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-245">Int64</span></span>|  
|<span data-ttu-id="2aadb-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2aadb-247">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-247">Int64</span></span>|  
|<span data-ttu-id="2aadb-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2aadb-249">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-249">Int32</span></span>|  
|<span data-ttu-id="2aadb-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2aadb-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="2aadb-251">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-251">Int16</span></span>|  
|<span data-ttu-id="2aadb-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-252">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-253">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-253">String</span></span>|  
|<span data-ttu-id="2aadb-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-254">TYPE_NAME</span></span>|<span data-ttu-id="2aadb-255">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-255">String</span></span>|  
|<span data-ttu-id="2aadb-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="2aadb-257">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="2aadb-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="2aadb-258">Catalog</span></span>  
  
|<span data-ttu-id="2aadb-259">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-259">ColumnName</span></span>|<span data-ttu-id="2aadb-260">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-261">CATALOG_NAME</span></span>|<span data-ttu-id="2aadb-262">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-262">String</span></span>|  
|<span data-ttu-id="2aadb-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-263">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-264">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2aadb-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-265">Indexes</span></span>  
  
|<span data-ttu-id="2aadb-266">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-266">ColumnName</span></span>|<span data-ttu-id="2aadb-267">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-268">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-269">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-269">String</span></span>|  
|<span data-ttu-id="2aadb-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-271">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-271">String</span></span>|  
|<span data-ttu-id="2aadb-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-272">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-273">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-273">String</span></span>|  
|<span data-ttu-id="2aadb-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-274">INDEX_CATALOG</span></span>|<span data-ttu-id="2aadb-275">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-275">String</span></span>|  
|<span data-ttu-id="2aadb-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="2aadb-277">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-277">String</span></span>|  
|<span data-ttu-id="2aadb-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-278">INDEX_NAME</span></span>|<span data-ttu-id="2aadb-279">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-279">String</span></span>|  
|<span data-ttu-id="2aadb-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2aadb-280">PRIMARY_KEY</span></span>|<span data-ttu-id="2aadb-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-281">Boolean</span></span>|  
|<span data-ttu-id="2aadb-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2aadb-282">UNIQUE</span></span>|<span data-ttu-id="2aadb-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-283">Boolean</span></span>|  
|<span data-ttu-id="2aadb-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2aadb-284">CLUSTERED</span></span>|<span data-ttu-id="2aadb-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-285">Boolean</span></span>|  
|<span data-ttu-id="2aadb-286">TYP</span><span class="sxs-lookup"><span data-stu-id="2aadb-286">TYPE</span></span>|<span data-ttu-id="2aadb-287">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-287">Int32</span></span>|  
|<span data-ttu-id="2aadb-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2aadb-288">FILL_FACTOR</span></span>|<span data-ttu-id="2aadb-289">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-289">Int32</span></span>|  
|<span data-ttu-id="2aadb-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2aadb-290">INITIAL_SIZE</span></span>|<span data-ttu-id="2aadb-291">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-291">Int32</span></span>|  
|<span data-ttu-id="2aadb-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2aadb-292">NULLS</span></span>|<span data-ttu-id="2aadb-293">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-293">Int32</span></span>|  
|<span data-ttu-id="2aadb-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2aadb-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2aadb-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-295">Boolean</span></span>|  
|<span data-ttu-id="2aadb-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2aadb-296">AUTO_UPDATE</span></span>|<span data-ttu-id="2aadb-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-297">Boolean</span></span>|  
|<span data-ttu-id="2aadb-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2aadb-298">NULL_COLLATION</span></span>|<span data-ttu-id="2aadb-299">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-299">Int32</span></span>|  
|<span data-ttu-id="2aadb-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-301">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-301">Int64</span></span>|  
|<span data-ttu-id="2aadb-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-302">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-303">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-303">String</span></span>|  
|<span data-ttu-id="2aadb-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-304">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-305">Guid</span></span>|  
|<span data-ttu-id="2aadb-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-306">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-307">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-307">Int64</span></span>|  
|<span data-ttu-id="2aadb-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2aadb-308">COLLATION</span></span>|<span data-ttu-id="2aadb-309">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-309">Int16</span></span>|  
|<span data-ttu-id="2aadb-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2aadb-310">CARDINALITY</span></span>|<span data-ttu-id="2aadb-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2aadb-311">Decimal</span></span>|  
|<span data-ttu-id="2aadb-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="2aadb-312">PAGES</span></span>|<span data-ttu-id="2aadb-313">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-313">Int32</span></span>|  
|<span data-ttu-id="2aadb-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-314">FILTER_CONDITION</span></span>|<span data-ttu-id="2aadb-315">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-315">String</span></span>|  
|<span data-ttu-id="2aadb-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-316">INTEGRATED</span></span>|<span data-ttu-id="2aadb-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="2aadb-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="2aadb-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="2aadb-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2aadb-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2aadb-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-320">Tables</span></span>  
  
-   <span data-ttu-id="2aadb-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-321">Columns</span></span>  
  
-   <span data-ttu-id="2aadb-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-322">Procedures</span></span>  
  
-   <span data-ttu-id="2aadb-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2aadb-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="2aadb-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="2aadb-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="2aadb-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="2aadb-325">Views</span></span>  
  
-   <span data-ttu-id="2aadb-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2aadb-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-327">Tables</span></span>  
  
|<span data-ttu-id="2aadb-328">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-328">ColumnName</span></span>|<span data-ttu-id="2aadb-329">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-330">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-331">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-331">String</span></span>|  
|<span data-ttu-id="2aadb-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-333">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-333">String</span></span>|  
|<span data-ttu-id="2aadb-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-334">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-335">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-335">String</span></span>|  
|<span data-ttu-id="2aadb-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-336">TABLE_TYPE</span></span>|<span data-ttu-id="2aadb-337">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-337">String</span></span>|  
|<span data-ttu-id="2aadb-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-338">TABLE_GUID</span></span>|<span data-ttu-id="2aadb-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-339">Guid</span></span>|  
|<span data-ttu-id="2aadb-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-340">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-341">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-341">String</span></span>|  
|<span data-ttu-id="2aadb-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-342">TABLE_PROPID</span></span>|<span data-ttu-id="2aadb-343">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-343">Int64</span></span>|  
|<span data-ttu-id="2aadb-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-344">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-345">DateTime</span></span>|  
|<span data-ttu-id="2aadb-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-346">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2aadb-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-348">Columns</span></span>  
  
|<span data-ttu-id="2aadb-349">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-349">ColumnName</span></span>|<span data-ttu-id="2aadb-350">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-351">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-352">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-352">String</span></span>|  
|<span data-ttu-id="2aadb-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-354">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-354">String</span></span>|  
|<span data-ttu-id="2aadb-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-355">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-356">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-356">String</span></span>|  
|<span data-ttu-id="2aadb-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-357">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-358">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-358">String</span></span>|  
|<span data-ttu-id="2aadb-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-359">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-360">Guid</span></span>|  
|<span data-ttu-id="2aadb-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-361">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-362">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-362">Int64</span></span>|  
|<span data-ttu-id="2aadb-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-364">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-364">Int64</span></span>|  
|<span data-ttu-id="2aadb-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2aadb-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-366">Boolean</span></span>|  
|<span data-ttu-id="2aadb-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2aadb-368">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-368">String</span></span>|  
|<span data-ttu-id="2aadb-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2aadb-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="2aadb-370">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-370">Int64</span></span>|  
|<span data-ttu-id="2aadb-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-371">IS_NULLABLE</span></span>|<span data-ttu-id="2aadb-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-372">Boolean</span></span>|  
|<span data-ttu-id="2aadb-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-373">DATA_TYPE</span></span>|<span data-ttu-id="2aadb-374">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-374">Int32</span></span>|  
|<span data-ttu-id="2aadb-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-375">TYPE_GUID</span></span>|<span data-ttu-id="2aadb-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-376">Guid</span></span>|  
|<span data-ttu-id="2aadb-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2aadb-378">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-378">Int64</span></span>|  
|<span data-ttu-id="2aadb-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2aadb-380">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-380">Int64</span></span>|  
|<span data-ttu-id="2aadb-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2aadb-382">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-382">Int32</span></span>|  
|<span data-ttu-id="2aadb-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2aadb-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="2aadb-384">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-384">Int16</span></span>|  
|<span data-ttu-id="2aadb-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="2aadb-386">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-386">Int64</span></span>|  
|<span data-ttu-id="2aadb-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2aadb-388">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-388">String</span></span>|  
|<span data-ttu-id="2aadb-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2aadb-390">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-390">String</span></span>|  
|<span data-ttu-id="2aadb-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2aadb-392">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-392">String</span></span>|  
|<span data-ttu-id="2aadb-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="2aadb-394">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-394">String</span></span>|  
|<span data-ttu-id="2aadb-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2aadb-396">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-396">String</span></span>|  
|<span data-ttu-id="2aadb-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-397">COLLATION_NAME</span></span>|<span data-ttu-id="2aadb-398">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-398">String</span></span>|  
|<span data-ttu-id="2aadb-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2aadb-400">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-400">String</span></span>|  
|<span data-ttu-id="2aadb-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2aadb-402">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-402">String</span></span>|  
|<span data-ttu-id="2aadb-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-403">DOMAIN_NAME</span></span>|<span data-ttu-id="2aadb-404">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-404">String</span></span>|  
|<span data-ttu-id="2aadb-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-405">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-406">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2aadb-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-407">Procedures</span></span>  
  
|<span data-ttu-id="2aadb-408">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-408">ColumnName</span></span>|<span data-ttu-id="2aadb-409">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2aadb-411">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-411">String</span></span>|  
|<span data-ttu-id="2aadb-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2aadb-413">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-413">String</span></span>|  
|<span data-ttu-id="2aadb-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="2aadb-415">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-415">String</span></span>|  
|<span data-ttu-id="2aadb-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2aadb-417">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-417">Int16</span></span>|  
|<span data-ttu-id="2aadb-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2aadb-419">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-419">String</span></span>|  
|<span data-ttu-id="2aadb-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-420">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-421">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-421">String</span></span>|  
|<span data-ttu-id="2aadb-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-422">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-423">DateTime</span></span>|  
|<span data-ttu-id="2aadb-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-424">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="2aadb-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="2aadb-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="2aadb-427">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-427">ColumnName</span></span>|<span data-ttu-id="2aadb-428">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2aadb-430">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-430">String</span></span>|  
|<span data-ttu-id="2aadb-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2aadb-432">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-432">String</span></span>|  
|<span data-ttu-id="2aadb-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="2aadb-434">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-434">String</span></span>|  
|<span data-ttu-id="2aadb-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-435">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-436">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-436">String</span></span>|  
|<span data-ttu-id="2aadb-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-437">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-438">Guid</span></span>|  
|<span data-ttu-id="2aadb-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-439">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-440">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-440">Int64</span></span>|  
|<span data-ttu-id="2aadb-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="2aadb-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="2aadb-442">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-442">Int64</span></span>|  
|<span data-ttu-id="2aadb-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-444">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-444">Int64</span></span>|  
|<span data-ttu-id="2aadb-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-445">IS_NULLABLE</span></span>|<span data-ttu-id="2aadb-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-446">Boolean</span></span>|  
|<span data-ttu-id="2aadb-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-447">DATA_TYPE</span></span>|<span data-ttu-id="2aadb-448">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-448">Int32</span></span>|  
|<span data-ttu-id="2aadb-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-449">TYPE_GUID</span></span>|<span data-ttu-id="2aadb-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-450">Guid</span></span>|  
|<span data-ttu-id="2aadb-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2aadb-452">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-452">Int64</span></span>|  
|<span data-ttu-id="2aadb-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2aadb-454">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-454">Int64</span></span>|  
|<span data-ttu-id="2aadb-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2aadb-456">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-456">Int32</span></span>|  
|<span data-ttu-id="2aadb-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2aadb-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="2aadb-458">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-458">Int16</span></span>|  
|<span data-ttu-id="2aadb-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-459">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-460">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-460">String</span></span>|  
|<span data-ttu-id="2aadb-461">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="2aadb-461">OVERLOAD</span></span>|<span data-ttu-id="2aadb-462">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="2aadb-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="2aadb-463">Views</span></span>  
  
|<span data-ttu-id="2aadb-464">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-464">ColumnName</span></span>|<span data-ttu-id="2aadb-465">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-466">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-467">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-467">String</span></span>|  
|<span data-ttu-id="2aadb-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-469">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-469">String</span></span>|  
|<span data-ttu-id="2aadb-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-470">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-471">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-471">String</span></span>|  
|<span data-ttu-id="2aadb-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="2aadb-473">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-473">String</span></span>|  
|<span data-ttu-id="2aadb-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="2aadb-474">CHECK_OPTION</span></span>|<span data-ttu-id="2aadb-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-475">Boolean</span></span>|  
|<span data-ttu-id="2aadb-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-476">IS_UPDATABLE</span></span>|<span data-ttu-id="2aadb-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-477">Boolean</span></span>|  
|<span data-ttu-id="2aadb-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-478">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-479">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-479">String</span></span>|  
|<span data-ttu-id="2aadb-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-480">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-481">DateTime</span></span>|  
|<span data-ttu-id="2aadb-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-482">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2aadb-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-484">Indexes</span></span>  
  
|<span data-ttu-id="2aadb-485">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-485">ColumnName</span></span>|<span data-ttu-id="2aadb-486">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-487">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-488">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-488">String</span></span>|  
|<span data-ttu-id="2aadb-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-490">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-490">String</span></span>|  
|<span data-ttu-id="2aadb-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-491">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-492">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-492">String</span></span>|  
|<span data-ttu-id="2aadb-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-493">INDEX_CATALOG</span></span>|<span data-ttu-id="2aadb-494">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-494">String</span></span>|  
|<span data-ttu-id="2aadb-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="2aadb-496">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-496">String</span></span>|  
|<span data-ttu-id="2aadb-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-497">INDEX_NAME</span></span>|<span data-ttu-id="2aadb-498">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-498">String</span></span>|  
|<span data-ttu-id="2aadb-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2aadb-499">PRIMARY_KEY</span></span>|<span data-ttu-id="2aadb-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-500">Boolean</span></span>|  
|<span data-ttu-id="2aadb-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2aadb-501">UNIQUE</span></span>|<span data-ttu-id="2aadb-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-502">Boolean</span></span>|  
|<span data-ttu-id="2aadb-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2aadb-503">CLUSTERED</span></span>|<span data-ttu-id="2aadb-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-504">Boolean</span></span>|  
|<span data-ttu-id="2aadb-505">TYP</span><span class="sxs-lookup"><span data-stu-id="2aadb-505">TYPE</span></span>|<span data-ttu-id="2aadb-506">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-506">Int32</span></span>|  
|<span data-ttu-id="2aadb-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2aadb-507">FILL_FACTOR</span></span>|<span data-ttu-id="2aadb-508">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-508">Int32</span></span>|  
|<span data-ttu-id="2aadb-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2aadb-509">INITIAL_SIZE</span></span>|<span data-ttu-id="2aadb-510">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-510">Int32</span></span>|  
|<span data-ttu-id="2aadb-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2aadb-511">NULLS</span></span>|<span data-ttu-id="2aadb-512">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-512">Int32</span></span>|  
|<span data-ttu-id="2aadb-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2aadb-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2aadb-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-514">Boolean</span></span>|  
|<span data-ttu-id="2aadb-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2aadb-515">AUTO_UPDATE</span></span>|<span data-ttu-id="2aadb-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-516">Boolean</span></span>|  
|<span data-ttu-id="2aadb-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2aadb-517">NULL_COLLATION</span></span>|<span data-ttu-id="2aadb-518">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-518">Int32</span></span>|  
|<span data-ttu-id="2aadb-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-520">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-520">Int64</span></span>|  
|<span data-ttu-id="2aadb-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-521">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-522">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-522">String</span></span>|  
|<span data-ttu-id="2aadb-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-523">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-524">Guid</span></span>|  
|<span data-ttu-id="2aadb-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-525">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-526">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-526">Int64</span></span>|  
|<span data-ttu-id="2aadb-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2aadb-527">COLLATION</span></span>|<span data-ttu-id="2aadb-528">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-528">Int16</span></span>|  
|<span data-ttu-id="2aadb-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2aadb-529">CARDINALITY</span></span>|<span data-ttu-id="2aadb-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2aadb-530">Decimal</span></span>|  
|<span data-ttu-id="2aadb-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="2aadb-531">PAGES</span></span>|<span data-ttu-id="2aadb-532">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-532">Int32</span></span>|  
|<span data-ttu-id="2aadb-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-533">FILTER_CONDITION</span></span>|<span data-ttu-id="2aadb-534">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-534">String</span></span>|  
|<span data-ttu-id="2aadb-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-535">INTEGRATED</span></span>|<span data-ttu-id="2aadb-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="2aadb-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="2aadb-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="2aadb-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="2aadb-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="2aadb-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-539">Tables</span></span>  
  
-   <span data-ttu-id="2aadb-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-540">Columns</span></span>  
  
-   <span data-ttu-id="2aadb-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-541">Procedures</span></span>  
  
-   <span data-ttu-id="2aadb-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="2aadb-542">Views</span></span>  
  
-   <span data-ttu-id="2aadb-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="2aadb-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="2aadb-544">Tables</span></span>  
  
|<span data-ttu-id="2aadb-545">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-545">ColumnName</span></span>|<span data-ttu-id="2aadb-546">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-547">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-548">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-548">String</span></span>|  
|<span data-ttu-id="2aadb-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-550">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-550">String</span></span>|  
|<span data-ttu-id="2aadb-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-551">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-552">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-552">String</span></span>|  
|<span data-ttu-id="2aadb-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-553">TABLE_TYPE</span></span>|<span data-ttu-id="2aadb-554">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-554">String</span></span>|  
|<span data-ttu-id="2aadb-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-555">TABLE_GUID</span></span>|<span data-ttu-id="2aadb-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-556">Guid</span></span>|  
|<span data-ttu-id="2aadb-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-557">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-558">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-558">String</span></span>|  
|<span data-ttu-id="2aadb-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-559">TABLE_PROPID</span></span>|<span data-ttu-id="2aadb-560">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-560">Int64</span></span>|  
|<span data-ttu-id="2aadb-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-561">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-562">DateTime</span></span>|  
|<span data-ttu-id="2aadb-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-563">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="2aadb-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-565">Columns</span></span>  
  
|<span data-ttu-id="2aadb-566">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-566">ColumnName</span></span>|<span data-ttu-id="2aadb-567">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-568">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-569">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-569">String</span></span>|  
|<span data-ttu-id="2aadb-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-571">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-571">String</span></span>|  
|<span data-ttu-id="2aadb-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-572">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-573">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-573">String</span></span>|  
|<span data-ttu-id="2aadb-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-574">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-575">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-575">String</span></span>|  
|<span data-ttu-id="2aadb-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-576">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-577">Guid</span></span>|  
|<span data-ttu-id="2aadb-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-578">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-579">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-579">Int64</span></span>|  
|<span data-ttu-id="2aadb-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-581">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-581">Int64</span></span>|  
|<span data-ttu-id="2aadb-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="2aadb-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-583">Boolean</span></span>|  
|<span data-ttu-id="2aadb-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="2aadb-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="2aadb-585">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-585">String</span></span>|  
|<span data-ttu-id="2aadb-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="2aadb-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="2aadb-587">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-587">Int64</span></span>|  
|<span data-ttu-id="2aadb-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-588">IS_NULLABLE</span></span>|<span data-ttu-id="2aadb-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-589">Boolean</span></span>|  
|<span data-ttu-id="2aadb-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-590">DATA_TYPE</span></span>|<span data-ttu-id="2aadb-591">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-591">Int32</span></span>|  
|<span data-ttu-id="2aadb-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-592">TYPE_GUID</span></span>|<span data-ttu-id="2aadb-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-593">Guid</span></span>|  
|<span data-ttu-id="2aadb-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="2aadb-595">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-595">Int64</span></span>|  
|<span data-ttu-id="2aadb-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="2aadb-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="2aadb-597">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-597">Int64</span></span>|  
|<span data-ttu-id="2aadb-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="2aadb-599">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-599">Int32</span></span>|  
|<span data-ttu-id="2aadb-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="2aadb-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="2aadb-601">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-601">Int16</span></span>|  
|<span data-ttu-id="2aadb-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="2aadb-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="2aadb-603">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-603">Int64</span></span>|  
|<span data-ttu-id="2aadb-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="2aadb-605">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-605">String</span></span>|  
|<span data-ttu-id="2aadb-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="2aadb-607">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-607">String</span></span>|  
|<span data-ttu-id="2aadb-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="2aadb-609">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-609">String</span></span>|  
|<span data-ttu-id="2aadb-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="2aadb-611">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-611">String</span></span>|  
|<span data-ttu-id="2aadb-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="2aadb-613">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-613">String</span></span>|  
|<span data-ttu-id="2aadb-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-614">COLLATION_NAME</span></span>|<span data-ttu-id="2aadb-615">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-615">String</span></span>|  
|<span data-ttu-id="2aadb-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="2aadb-617">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-617">String</span></span>|  
|<span data-ttu-id="2aadb-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="2aadb-619">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-619">String</span></span>|  
|<span data-ttu-id="2aadb-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-620">DOMAIN_NAME</span></span>|<span data-ttu-id="2aadb-621">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-621">String</span></span>|  
|<span data-ttu-id="2aadb-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-622">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-623">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="2aadb-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="2aadb-624">Procedures</span></span>  
  
|<span data-ttu-id="2aadb-625">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-625">ColumnName</span></span>|<span data-ttu-id="2aadb-626">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="2aadb-628">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-628">String</span></span>|  
|<span data-ttu-id="2aadb-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="2aadb-630">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-630">String</span></span>|  
|<span data-ttu-id="2aadb-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="2aadb-632">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-632">String</span></span>|  
|<span data-ttu-id="2aadb-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="2aadb-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="2aadb-634">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-634">Int16</span></span>|  
|<span data-ttu-id="2aadb-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="2aadb-636">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-636">String</span></span>|  
|<span data-ttu-id="2aadb-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-637">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-638">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-638">String</span></span>|  
|<span data-ttu-id="2aadb-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-639">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-640">DateTime</span></span>|  
|<span data-ttu-id="2aadb-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-641">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="2aadb-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="2aadb-643">Views</span></span>  
  
|<span data-ttu-id="2aadb-644">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-644">ColumnName</span></span>|<span data-ttu-id="2aadb-645">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-646">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-647">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-647">String</span></span>|  
|<span data-ttu-id="2aadb-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-649">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-649">String</span></span>|  
|<span data-ttu-id="2aadb-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-650">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-651">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-651">String</span></span>|  
|<span data-ttu-id="2aadb-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="2aadb-653">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-653">String</span></span>|  
|<span data-ttu-id="2aadb-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="2aadb-654">CHECK_OPTION</span></span>|<span data-ttu-id="2aadb-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-655">Boolean</span></span>|  
|<span data-ttu-id="2aadb-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="2aadb-656">IS_UPDATABLE</span></span>|<span data-ttu-id="2aadb-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-657">Boolean</span></span>|  
|<span data-ttu-id="2aadb-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="2aadb-658">DESCRIPTION</span></span>|<span data-ttu-id="2aadb-659">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-659">String</span></span>|  
|<span data-ttu-id="2aadb-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-660">DATE_CREATED</span></span>|<span data-ttu-id="2aadb-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-661">DateTime</span></span>|  
|<span data-ttu-id="2aadb-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="2aadb-662">DATE_MODIFIED</span></span>|<span data-ttu-id="2aadb-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="2aadb-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="2aadb-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="2aadb-664">Indexes</span></span>  
  
|<span data-ttu-id="2aadb-665">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="2aadb-665">ColumnName</span></span>|<span data-ttu-id="2aadb-666">DataType</span><span class="sxs-lookup"><span data-stu-id="2aadb-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="2aadb-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-667">TABLE_CATALOG</span></span>|<span data-ttu-id="2aadb-668">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-668">String</span></span>|  
|<span data-ttu-id="2aadb-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="2aadb-670">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-670">String</span></span>|  
|<span data-ttu-id="2aadb-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-671">TABLE_NAME</span></span>|<span data-ttu-id="2aadb-672">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-672">String</span></span>|  
|<span data-ttu-id="2aadb-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="2aadb-673">INDEX_CATALOG</span></span>|<span data-ttu-id="2aadb-674">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-674">String</span></span>|  
|<span data-ttu-id="2aadb-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="2aadb-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="2aadb-676">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-676">String</span></span>|  
|<span data-ttu-id="2aadb-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-677">INDEX_NAME</span></span>|<span data-ttu-id="2aadb-678">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-678">String</span></span>|  
|<span data-ttu-id="2aadb-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="2aadb-679">PRIMARY_KEY</span></span>|<span data-ttu-id="2aadb-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-680">Boolean</span></span>|  
|<span data-ttu-id="2aadb-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="2aadb-681">UNIQUE</span></span>|<span data-ttu-id="2aadb-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-682">Boolean</span></span>|  
|<span data-ttu-id="2aadb-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="2aadb-683">CLUSTERED</span></span>|<span data-ttu-id="2aadb-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-684">Boolean</span></span>|  
|<span data-ttu-id="2aadb-685">TYP</span><span class="sxs-lookup"><span data-stu-id="2aadb-685">TYPE</span></span>|<span data-ttu-id="2aadb-686">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-686">Int32</span></span>|  
|<span data-ttu-id="2aadb-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="2aadb-687">FILL_FACTOR</span></span>|<span data-ttu-id="2aadb-688">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-688">Int32</span></span>|  
|<span data-ttu-id="2aadb-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="2aadb-689">INITIAL_SIZE</span></span>|<span data-ttu-id="2aadb-690">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-690">Int32</span></span>|  
|<span data-ttu-id="2aadb-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="2aadb-691">NULLS</span></span>|<span data-ttu-id="2aadb-692">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-692">Int32</span></span>|  
|<span data-ttu-id="2aadb-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="2aadb-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="2aadb-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-694">Boolean</span></span>|  
|<span data-ttu-id="2aadb-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="2aadb-695">AUTO_UPDATE</span></span>|<span data-ttu-id="2aadb-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-696">Boolean</span></span>|  
|<span data-ttu-id="2aadb-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="2aadb-697">NULL_COLLATION</span></span>|<span data-ttu-id="2aadb-698">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-698">Int32</span></span>|  
|<span data-ttu-id="2aadb-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="2aadb-700">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-700">Int64</span></span>|  
|<span data-ttu-id="2aadb-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="2aadb-701">COLUMN_NAME</span></span>|<span data-ttu-id="2aadb-702">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-702">String</span></span>|  
|<span data-ttu-id="2aadb-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-703">COLUMN_GUID</span></span>|<span data-ttu-id="2aadb-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="2aadb-704">Guid</span></span>|  
|<span data-ttu-id="2aadb-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="2aadb-705">COLUMN_PROPID</span></span>|<span data-ttu-id="2aadb-706">Int64</span><span class="sxs-lookup"><span data-stu-id="2aadb-706">Int64</span></span>|  
|<span data-ttu-id="2aadb-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="2aadb-707">COLLATION</span></span>|<span data-ttu-id="2aadb-708">Int16</span><span class="sxs-lookup"><span data-stu-id="2aadb-708">Int16</span></span>|  
|<span data-ttu-id="2aadb-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="2aadb-709">CARDINALITY</span></span>|<span data-ttu-id="2aadb-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="2aadb-710">Decimal</span></span>|  
|<span data-ttu-id="2aadb-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="2aadb-711">PAGES</span></span>|<span data-ttu-id="2aadb-712">Int32</span><span class="sxs-lookup"><span data-stu-id="2aadb-712">Int32</span></span>|  
|<span data-ttu-id="2aadb-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="2aadb-713">FILTER_CONDITION</span></span>|<span data-ttu-id="2aadb-714">String</span><span class="sxs-lookup"><span data-stu-id="2aadb-714">String</span></span>|  
|<span data-ttu-id="2aadb-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="2aadb-715">INTEGRATED</span></span>|<span data-ttu-id="2aadb-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="2aadb-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2aadb-717">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2aadb-717">See also</span></span>
- [<span data-ttu-id="2aadb-718">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2aadb-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
