---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514492"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0b990-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="0b990-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="0b990-103">W tej sekcji omówiono Obsługa kolekcję schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0b990-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0b990-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="0b990-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="0b990-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0b990-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b990-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-106">Tables</span></span>  
  
-   <span data-ttu-id="0b990-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-107">Columns</span></span>  
  
-   <span data-ttu-id="0b990-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-108">Procedures</span></span>  
  
-   <span data-ttu-id="0b990-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b990-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0b990-110">Wykaz</span><span class="sxs-lookup"><span data-stu-id="0b990-110">Catalog</span></span>  
  
-   <span data-ttu-id="0b990-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b990-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-112">Tables</span></span>  
  
|<span data-ttu-id="0b990-113">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-113">ColumnName</span></span>|<span data-ttu-id="0b990-114">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-116">String</span><span class="sxs-lookup"><span data-stu-id="0b990-116">String</span></span>|  
|<span data-ttu-id="0b990-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-118">String</span><span class="sxs-lookup"><span data-stu-id="0b990-118">String</span></span>|  
|<span data-ttu-id="0b990-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-119">TABLE_NAME</span></span>|<span data-ttu-id="0b990-120">String</span><span class="sxs-lookup"><span data-stu-id="0b990-120">String</span></span>|  
|<span data-ttu-id="0b990-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-121">TABLE_TYPE</span></span>|<span data-ttu-id="0b990-122">String</span><span class="sxs-lookup"><span data-stu-id="0b990-122">String</span></span>|  
|<span data-ttu-id="0b990-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-123">TABLE_GUID</span></span>|<span data-ttu-id="0b990-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-124">Guid</span></span>|  
|<span data-ttu-id="0b990-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-125">DESCRIPTION</span></span>|<span data-ttu-id="0b990-126">String</span><span class="sxs-lookup"><span data-stu-id="0b990-126">String</span></span>|  
|<span data-ttu-id="0b990-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-127">TABLE_PROPID</span></span>|<span data-ttu-id="0b990-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-128">Int64</span></span>|  
|<span data-ttu-id="0b990-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-129">DATE_CREATED</span></span>|<span data-ttu-id="0b990-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-130">DateTime</span></span>|  
|<span data-ttu-id="0b990-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b990-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-133">Columns</span></span>  
  
|<span data-ttu-id="0b990-134">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-134">ColumnName</span></span>|<span data-ttu-id="0b990-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-137">String</span><span class="sxs-lookup"><span data-stu-id="0b990-137">String</span></span>|  
|<span data-ttu-id="0b990-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-139">String</span><span class="sxs-lookup"><span data-stu-id="0b990-139">String</span></span>|  
|<span data-ttu-id="0b990-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-140">TABLE_NAME</span></span>|<span data-ttu-id="0b990-141">String</span><span class="sxs-lookup"><span data-stu-id="0b990-141">String</span></span>|  
|<span data-ttu-id="0b990-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-142">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-143">String</span><span class="sxs-lookup"><span data-stu-id="0b990-143">String</span></span>|  
|<span data-ttu-id="0b990-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-144">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-145">Guid</span></span>|  
|<span data-ttu-id="0b990-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-147">Int64</span></span>|  
|<span data-ttu-id="0b990-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-149">Int64</span></span>|  
|<span data-ttu-id="0b990-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b990-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-151">Boolean</span></span>|  
|<span data-ttu-id="0b990-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b990-153">String</span><span class="sxs-lookup"><span data-stu-id="0b990-153">String</span></span>|  
|<span data-ttu-id="0b990-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b990-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b990-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-155">Int64</span></span>|  
|<span data-ttu-id="0b990-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-156">IS_NULLABLE</span></span>|<span data-ttu-id="0b990-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-157">Boolean</span></span>|  
|<span data-ttu-id="0b990-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-158">DATA_TYPE</span></span>|<span data-ttu-id="0b990-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-159">Int32</span></span>|  
|<span data-ttu-id="0b990-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-160">TYPE_GUID</span></span>|<span data-ttu-id="0b990-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-161">Guid</span></span>|  
|<span data-ttu-id="0b990-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b990-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-163">Int64</span></span>|  
|<span data-ttu-id="0b990-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b990-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-165">Int64</span></span>|  
|<span data-ttu-id="0b990-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b990-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-167">Int32</span></span>|  
|<span data-ttu-id="0b990-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b990-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b990-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-169">Int16</span></span>|  
|<span data-ttu-id="0b990-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b990-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-171">Int64</span></span>|  
|<span data-ttu-id="0b990-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b990-173">String</span><span class="sxs-lookup"><span data-stu-id="0b990-173">String</span></span>|  
|<span data-ttu-id="0b990-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b990-175">String</span><span class="sxs-lookup"><span data-stu-id="0b990-175">String</span></span>|  
|<span data-ttu-id="0b990-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b990-177">String</span><span class="sxs-lookup"><span data-stu-id="0b990-177">String</span></span>|  
|<span data-ttu-id="0b990-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b990-179">String</span><span class="sxs-lookup"><span data-stu-id="0b990-179">String</span></span>|  
|<span data-ttu-id="0b990-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b990-181">String</span><span class="sxs-lookup"><span data-stu-id="0b990-181">String</span></span>|  
|<span data-ttu-id="0b990-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-182">COLLATION_NAME</span></span>|<span data-ttu-id="0b990-183">String</span><span class="sxs-lookup"><span data-stu-id="0b990-183">String</span></span>|  
|<span data-ttu-id="0b990-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b990-185">String</span><span class="sxs-lookup"><span data-stu-id="0b990-185">String</span></span>|  
|<span data-ttu-id="0b990-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b990-187">String</span><span class="sxs-lookup"><span data-stu-id="0b990-187">String</span></span>|  
|<span data-ttu-id="0b990-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0b990-189">String</span><span class="sxs-lookup"><span data-stu-id="0b990-189">String</span></span>|  
|<span data-ttu-id="0b990-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-190">DESCRIPTION</span></span>|<span data-ttu-id="0b990-191">String</span><span class="sxs-lookup"><span data-stu-id="0b990-191">String</span></span>|  
|<span data-ttu-id="0b990-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0b990-192">COLUMN_LCID</span></span>|<span data-ttu-id="0b990-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-193">Int32</span></span>|  
|<span data-ttu-id="0b990-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0b990-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0b990-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-195">Int32</span></span>|  
|<span data-ttu-id="0b990-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0b990-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0b990-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-197">Int32</span></span>|  
|<span data-ttu-id="0b990-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0b990-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0b990-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="0b990-199">Byte[]</span></span>|  
|<span data-ttu-id="0b990-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0b990-200">IS_COMPUTED</span></span>|<span data-ttu-id="0b990-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b990-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-202">Procedures</span></span>  
  
|<span data-ttu-id="0b990-203">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-203">ColumnName</span></span>|<span data-ttu-id="0b990-204">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b990-206">String</span><span class="sxs-lookup"><span data-stu-id="0b990-206">String</span></span>|  
|<span data-ttu-id="0b990-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b990-208">String</span><span class="sxs-lookup"><span data-stu-id="0b990-208">String</span></span>|  
|<span data-ttu-id="0b990-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b990-210">String</span><span class="sxs-lookup"><span data-stu-id="0b990-210">String</span></span>|  
|<span data-ttu-id="0b990-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b990-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-212">Int16</span></span>|  
|<span data-ttu-id="0b990-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b990-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b990-214">String</span><span class="sxs-lookup"><span data-stu-id="0b990-214">String</span></span>|  
|<span data-ttu-id="0b990-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-215">DESCRIPTION</span></span>|<span data-ttu-id="0b990-216">String</span><span class="sxs-lookup"><span data-stu-id="0b990-216">String</span></span>|  
|<span data-ttu-id="0b990-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-217">DATE_CREATED</span></span>|<span data-ttu-id="0b990-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-218">DateTime</span></span>|  
|<span data-ttu-id="0b990-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0b990-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b990-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0b990-222">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-222">ColumnName</span></span>|<span data-ttu-id="0b990-223">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b990-225">String</span><span class="sxs-lookup"><span data-stu-id="0b990-225">String</span></span>|  
|<span data-ttu-id="0b990-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b990-227">String</span><span class="sxs-lookup"><span data-stu-id="0b990-227">String</span></span>|  
|<span data-ttu-id="0b990-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b990-229">String</span><span class="sxs-lookup"><span data-stu-id="0b990-229">String</span></span>|  
|<span data-ttu-id="0b990-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0b990-231">String</span><span class="sxs-lookup"><span data-stu-id="0b990-231">String</span></span>|  
|<span data-ttu-id="0b990-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-233">Int32</span></span>|  
|<span data-ttu-id="0b990-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="0b990-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0b990-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-235">Int32</span></span>|  
|<span data-ttu-id="0b990-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0b990-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-237">Boolean</span></span>|  
|<span data-ttu-id="0b990-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0b990-239">String</span><span class="sxs-lookup"><span data-stu-id="0b990-239">String</span></span>|  
|<span data-ttu-id="0b990-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-240">IS_NULLABLE</span></span>|<span data-ttu-id="0b990-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-241">Boolean</span></span>|  
|<span data-ttu-id="0b990-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-242">DATA_TYPE</span></span>|<span data-ttu-id="0b990-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-243">Int32</span></span>|  
|<span data-ttu-id="0b990-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b990-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-245">Int64</span></span>|  
|<span data-ttu-id="0b990-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b990-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-247">Int64</span></span>|  
|<span data-ttu-id="0b990-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b990-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-249">Int32</span></span>|  
|<span data-ttu-id="0b990-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b990-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b990-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-251">Int16</span></span>|  
|<span data-ttu-id="0b990-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-252">DESCRIPTION</span></span>|<span data-ttu-id="0b990-253">String</span><span class="sxs-lookup"><span data-stu-id="0b990-253">String</span></span>|  
|<span data-ttu-id="0b990-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-254">TYPE_NAME</span></span>|<span data-ttu-id="0b990-255">String</span><span class="sxs-lookup"><span data-stu-id="0b990-255">String</span></span>|  
|<span data-ttu-id="0b990-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0b990-257">String</span><span class="sxs-lookup"><span data-stu-id="0b990-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0b990-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="0b990-258">Catalog</span></span>  
  
|<span data-ttu-id="0b990-259">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-259">ColumnName</span></span>|<span data-ttu-id="0b990-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-261">CATALOG_NAME</span></span>|<span data-ttu-id="0b990-262">String</span><span class="sxs-lookup"><span data-stu-id="0b990-262">String</span></span>|  
|<span data-ttu-id="0b990-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-263">DESCRIPTION</span></span>|<span data-ttu-id="0b990-264">String</span><span class="sxs-lookup"><span data-stu-id="0b990-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b990-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-265">Indexes</span></span>  
  
|<span data-ttu-id="0b990-266">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-266">ColumnName</span></span>|<span data-ttu-id="0b990-267">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-269">String</span><span class="sxs-lookup"><span data-stu-id="0b990-269">String</span></span>|  
|<span data-ttu-id="0b990-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-271">String</span><span class="sxs-lookup"><span data-stu-id="0b990-271">String</span></span>|  
|<span data-ttu-id="0b990-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-272">TABLE_NAME</span></span>|<span data-ttu-id="0b990-273">String</span><span class="sxs-lookup"><span data-stu-id="0b990-273">String</span></span>|  
|<span data-ttu-id="0b990-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0b990-275">String</span><span class="sxs-lookup"><span data-stu-id="0b990-275">String</span></span>|  
|<span data-ttu-id="0b990-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b990-277">String</span><span class="sxs-lookup"><span data-stu-id="0b990-277">String</span></span>|  
|<span data-ttu-id="0b990-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-278">INDEX_NAME</span></span>|<span data-ttu-id="0b990-279">String</span><span class="sxs-lookup"><span data-stu-id="0b990-279">String</span></span>|  
|<span data-ttu-id="0b990-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b990-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0b990-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-281">Boolean</span></span>|  
|<span data-ttu-id="0b990-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0b990-282">UNIQUE</span></span>|<span data-ttu-id="0b990-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-283">Boolean</span></span>|  
|<span data-ttu-id="0b990-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b990-284">CLUSTERED</span></span>|<span data-ttu-id="0b990-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-285">Boolean</span></span>|  
|<span data-ttu-id="0b990-286">TYP</span><span class="sxs-lookup"><span data-stu-id="0b990-286">TYPE</span></span>|<span data-ttu-id="0b990-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-287">Int32</span></span>|  
|<span data-ttu-id="0b990-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b990-288">FILL_FACTOR</span></span>|<span data-ttu-id="0b990-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-289">Int32</span></span>|  
|<span data-ttu-id="0b990-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b990-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0b990-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-291">Int32</span></span>|  
|<span data-ttu-id="0b990-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0b990-292">NULLS</span></span>|<span data-ttu-id="0b990-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-293">Int32</span></span>|  
|<span data-ttu-id="0b990-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b990-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b990-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-295">Boolean</span></span>|  
|<span data-ttu-id="0b990-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b990-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0b990-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-297">Boolean</span></span>|  
|<span data-ttu-id="0b990-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b990-298">NULL_COLLATION</span></span>|<span data-ttu-id="0b990-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-299">Int32</span></span>|  
|<span data-ttu-id="0b990-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-301">Int64</span></span>|  
|<span data-ttu-id="0b990-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-302">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-303">String</span><span class="sxs-lookup"><span data-stu-id="0b990-303">String</span></span>|  
|<span data-ttu-id="0b990-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-304">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-305">Guid</span></span>|  
|<span data-ttu-id="0b990-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-307">Int64</span></span>|  
|<span data-ttu-id="0b990-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0b990-308">COLLATION</span></span>|<span data-ttu-id="0b990-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-309">Int16</span></span>|  
|<span data-ttu-id="0b990-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0b990-310">CARDINALITY</span></span>|<span data-ttu-id="0b990-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0b990-311">Decimal</span></span>|  
|<span data-ttu-id="0b990-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="0b990-312">PAGES</span></span>|<span data-ttu-id="0b990-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-313">Int32</span></span>|  
|<span data-ttu-id="0b990-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b990-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0b990-315">String</span><span class="sxs-lookup"><span data-stu-id="0b990-315">String</span></span>|  
|<span data-ttu-id="0b990-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0b990-316">INTEGRATED</span></span>|<span data-ttu-id="0b990-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0b990-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="0b990-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="0b990-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0b990-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b990-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-320">Tables</span></span>  
  
-   <span data-ttu-id="0b990-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-321">Columns</span></span>  
  
-   <span data-ttu-id="0b990-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-322">Procedures</span></span>  
  
-   <span data-ttu-id="0b990-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0b990-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="0b990-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0b990-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="0b990-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="0b990-325">Views</span></span>  
  
-   <span data-ttu-id="0b990-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b990-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-327">Tables</span></span>  
  
|<span data-ttu-id="0b990-328">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-328">ColumnName</span></span>|<span data-ttu-id="0b990-329">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-331">String</span><span class="sxs-lookup"><span data-stu-id="0b990-331">String</span></span>|  
|<span data-ttu-id="0b990-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-333">String</span><span class="sxs-lookup"><span data-stu-id="0b990-333">String</span></span>|  
|<span data-ttu-id="0b990-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-334">TABLE_NAME</span></span>|<span data-ttu-id="0b990-335">String</span><span class="sxs-lookup"><span data-stu-id="0b990-335">String</span></span>|  
|<span data-ttu-id="0b990-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-336">TABLE_TYPE</span></span>|<span data-ttu-id="0b990-337">String</span><span class="sxs-lookup"><span data-stu-id="0b990-337">String</span></span>|  
|<span data-ttu-id="0b990-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-338">TABLE_GUID</span></span>|<span data-ttu-id="0b990-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-339">Guid</span></span>|  
|<span data-ttu-id="0b990-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-340">DESCRIPTION</span></span>|<span data-ttu-id="0b990-341">String</span><span class="sxs-lookup"><span data-stu-id="0b990-341">String</span></span>|  
|<span data-ttu-id="0b990-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-342">TABLE_PROPID</span></span>|<span data-ttu-id="0b990-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-343">Int64</span></span>|  
|<span data-ttu-id="0b990-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-344">DATE_CREATED</span></span>|<span data-ttu-id="0b990-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-345">DateTime</span></span>|  
|<span data-ttu-id="0b990-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b990-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-348">Columns</span></span>  
  
|<span data-ttu-id="0b990-349">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-349">ColumnName</span></span>|<span data-ttu-id="0b990-350">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-352">String</span><span class="sxs-lookup"><span data-stu-id="0b990-352">String</span></span>|  
|<span data-ttu-id="0b990-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-354">String</span><span class="sxs-lookup"><span data-stu-id="0b990-354">String</span></span>|  
|<span data-ttu-id="0b990-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-355">TABLE_NAME</span></span>|<span data-ttu-id="0b990-356">String</span><span class="sxs-lookup"><span data-stu-id="0b990-356">String</span></span>|  
|<span data-ttu-id="0b990-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-357">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-358">String</span><span class="sxs-lookup"><span data-stu-id="0b990-358">String</span></span>|  
|<span data-ttu-id="0b990-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-359">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-360">Guid</span></span>|  
|<span data-ttu-id="0b990-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-362">Int64</span></span>|  
|<span data-ttu-id="0b990-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-364">Int64</span></span>|  
|<span data-ttu-id="0b990-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b990-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-366">Boolean</span></span>|  
|<span data-ttu-id="0b990-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b990-368">String</span><span class="sxs-lookup"><span data-stu-id="0b990-368">String</span></span>|  
|<span data-ttu-id="0b990-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b990-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b990-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-370">Int64</span></span>|  
|<span data-ttu-id="0b990-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-371">IS_NULLABLE</span></span>|<span data-ttu-id="0b990-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-372">Boolean</span></span>|  
|<span data-ttu-id="0b990-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-373">DATA_TYPE</span></span>|<span data-ttu-id="0b990-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-374">Int32</span></span>|  
|<span data-ttu-id="0b990-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-375">TYPE_GUID</span></span>|<span data-ttu-id="0b990-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-376">Guid</span></span>|  
|<span data-ttu-id="0b990-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b990-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-378">Int64</span></span>|  
|<span data-ttu-id="0b990-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b990-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-380">Int64</span></span>|  
|<span data-ttu-id="0b990-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b990-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-382">Int32</span></span>|  
|<span data-ttu-id="0b990-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b990-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b990-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-384">Int16</span></span>|  
|<span data-ttu-id="0b990-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b990-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-386">Int64</span></span>|  
|<span data-ttu-id="0b990-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b990-388">String</span><span class="sxs-lookup"><span data-stu-id="0b990-388">String</span></span>|  
|<span data-ttu-id="0b990-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b990-390">String</span><span class="sxs-lookup"><span data-stu-id="0b990-390">String</span></span>|  
|<span data-ttu-id="0b990-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b990-392">String</span><span class="sxs-lookup"><span data-stu-id="0b990-392">String</span></span>|  
|<span data-ttu-id="0b990-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b990-394">String</span><span class="sxs-lookup"><span data-stu-id="0b990-394">String</span></span>|  
|<span data-ttu-id="0b990-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b990-396">String</span><span class="sxs-lookup"><span data-stu-id="0b990-396">String</span></span>|  
|<span data-ttu-id="0b990-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-397">COLLATION_NAME</span></span>|<span data-ttu-id="0b990-398">String</span><span class="sxs-lookup"><span data-stu-id="0b990-398">String</span></span>|  
|<span data-ttu-id="0b990-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b990-400">String</span><span class="sxs-lookup"><span data-stu-id="0b990-400">String</span></span>|  
|<span data-ttu-id="0b990-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b990-402">String</span><span class="sxs-lookup"><span data-stu-id="0b990-402">String</span></span>|  
|<span data-ttu-id="0b990-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0b990-404">String</span><span class="sxs-lookup"><span data-stu-id="0b990-404">String</span></span>|  
|<span data-ttu-id="0b990-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-405">DESCRIPTION</span></span>|<span data-ttu-id="0b990-406">String</span><span class="sxs-lookup"><span data-stu-id="0b990-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b990-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-407">Procedures</span></span>  
  
|<span data-ttu-id="0b990-408">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-408">ColumnName</span></span>|<span data-ttu-id="0b990-409">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b990-411">String</span><span class="sxs-lookup"><span data-stu-id="0b990-411">String</span></span>|  
|<span data-ttu-id="0b990-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b990-413">String</span><span class="sxs-lookup"><span data-stu-id="0b990-413">String</span></span>|  
|<span data-ttu-id="0b990-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b990-415">String</span><span class="sxs-lookup"><span data-stu-id="0b990-415">String</span></span>|  
|<span data-ttu-id="0b990-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b990-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-417">Int16</span></span>|  
|<span data-ttu-id="0b990-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b990-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b990-419">String</span><span class="sxs-lookup"><span data-stu-id="0b990-419">String</span></span>|  
|<span data-ttu-id="0b990-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-420">DESCRIPTION</span></span>|<span data-ttu-id="0b990-421">String</span><span class="sxs-lookup"><span data-stu-id="0b990-421">String</span></span>|  
|<span data-ttu-id="0b990-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-422">DATE_CREATED</span></span>|<span data-ttu-id="0b990-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-423">DateTime</span></span>|  
|<span data-ttu-id="0b990-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0b990-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0b990-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0b990-427">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-427">ColumnName</span></span>|<span data-ttu-id="0b990-428">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b990-430">String</span><span class="sxs-lookup"><span data-stu-id="0b990-430">String</span></span>|  
|<span data-ttu-id="0b990-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b990-432">String</span><span class="sxs-lookup"><span data-stu-id="0b990-432">String</span></span>|  
|<span data-ttu-id="0b990-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b990-434">String</span><span class="sxs-lookup"><span data-stu-id="0b990-434">String</span></span>|  
|<span data-ttu-id="0b990-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-435">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-436">String</span><span class="sxs-lookup"><span data-stu-id="0b990-436">String</span></span>|  
|<span data-ttu-id="0b990-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-437">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-438">Guid</span></span>|  
|<span data-ttu-id="0b990-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-440">Int64</span></span>|  
|<span data-ttu-id="0b990-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0b990-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0b990-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-442">Int64</span></span>|  
|<span data-ttu-id="0b990-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-444">Int64</span></span>|  
|<span data-ttu-id="0b990-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-445">IS_NULLABLE</span></span>|<span data-ttu-id="0b990-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-446">Boolean</span></span>|  
|<span data-ttu-id="0b990-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-447">DATA_TYPE</span></span>|<span data-ttu-id="0b990-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-448">Int32</span></span>|  
|<span data-ttu-id="0b990-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-449">TYPE_GUID</span></span>|<span data-ttu-id="0b990-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-450">Guid</span></span>|  
|<span data-ttu-id="0b990-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b990-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-452">Int64</span></span>|  
|<span data-ttu-id="0b990-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b990-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-454">Int64</span></span>|  
|<span data-ttu-id="0b990-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b990-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-456">Int32</span></span>|  
|<span data-ttu-id="0b990-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b990-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b990-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-458">Int16</span></span>|  
|<span data-ttu-id="0b990-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-459">DESCRIPTION</span></span>|<span data-ttu-id="0b990-460">String</span><span class="sxs-lookup"><span data-stu-id="0b990-460">String</span></span>|  
|<span data-ttu-id="0b990-461">PRZECIĄŻENIE</span><span class="sxs-lookup"><span data-stu-id="0b990-461">OVERLOAD</span></span>|<span data-ttu-id="0b990-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0b990-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="0b990-463">Views</span></span>  
  
|<span data-ttu-id="0b990-464">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-464">ColumnName</span></span>|<span data-ttu-id="0b990-465">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-467">String</span><span class="sxs-lookup"><span data-stu-id="0b990-467">String</span></span>|  
|<span data-ttu-id="0b990-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-469">String</span><span class="sxs-lookup"><span data-stu-id="0b990-469">String</span></span>|  
|<span data-ttu-id="0b990-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-470">TABLE_NAME</span></span>|<span data-ttu-id="0b990-471">String</span><span class="sxs-lookup"><span data-stu-id="0b990-471">String</span></span>|  
|<span data-ttu-id="0b990-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b990-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0b990-473">String</span><span class="sxs-lookup"><span data-stu-id="0b990-473">String</span></span>|  
|<span data-ttu-id="0b990-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0b990-474">CHECK_OPTION</span></span>|<span data-ttu-id="0b990-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-475">Boolean</span></span>|  
|<span data-ttu-id="0b990-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0b990-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-477">Boolean</span></span>|  
|<span data-ttu-id="0b990-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-478">DESCRIPTION</span></span>|<span data-ttu-id="0b990-479">String</span><span class="sxs-lookup"><span data-stu-id="0b990-479">String</span></span>|  
|<span data-ttu-id="0b990-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-480">DATE_CREATED</span></span>|<span data-ttu-id="0b990-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-481">DateTime</span></span>|  
|<span data-ttu-id="0b990-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b990-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-484">Indexes</span></span>  
  
|<span data-ttu-id="0b990-485">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-485">ColumnName</span></span>|<span data-ttu-id="0b990-486">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-488">String</span><span class="sxs-lookup"><span data-stu-id="0b990-488">String</span></span>|  
|<span data-ttu-id="0b990-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-490">String</span><span class="sxs-lookup"><span data-stu-id="0b990-490">String</span></span>|  
|<span data-ttu-id="0b990-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-491">TABLE_NAME</span></span>|<span data-ttu-id="0b990-492">String</span><span class="sxs-lookup"><span data-stu-id="0b990-492">String</span></span>|  
|<span data-ttu-id="0b990-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0b990-494">String</span><span class="sxs-lookup"><span data-stu-id="0b990-494">String</span></span>|  
|<span data-ttu-id="0b990-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b990-496">String</span><span class="sxs-lookup"><span data-stu-id="0b990-496">String</span></span>|  
|<span data-ttu-id="0b990-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-497">INDEX_NAME</span></span>|<span data-ttu-id="0b990-498">String</span><span class="sxs-lookup"><span data-stu-id="0b990-498">String</span></span>|  
|<span data-ttu-id="0b990-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b990-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0b990-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-500">Boolean</span></span>|  
|<span data-ttu-id="0b990-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0b990-501">UNIQUE</span></span>|<span data-ttu-id="0b990-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-502">Boolean</span></span>|  
|<span data-ttu-id="0b990-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b990-503">CLUSTERED</span></span>|<span data-ttu-id="0b990-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-504">Boolean</span></span>|  
|<span data-ttu-id="0b990-505">TYP</span><span class="sxs-lookup"><span data-stu-id="0b990-505">TYPE</span></span>|<span data-ttu-id="0b990-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-506">Int32</span></span>|  
|<span data-ttu-id="0b990-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b990-507">FILL_FACTOR</span></span>|<span data-ttu-id="0b990-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-508">Int32</span></span>|  
|<span data-ttu-id="0b990-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b990-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0b990-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-510">Int32</span></span>|  
|<span data-ttu-id="0b990-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0b990-511">NULLS</span></span>|<span data-ttu-id="0b990-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-512">Int32</span></span>|  
|<span data-ttu-id="0b990-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b990-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b990-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-514">Boolean</span></span>|  
|<span data-ttu-id="0b990-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b990-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0b990-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-516">Boolean</span></span>|  
|<span data-ttu-id="0b990-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b990-517">NULL_COLLATION</span></span>|<span data-ttu-id="0b990-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-518">Int32</span></span>|  
|<span data-ttu-id="0b990-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-520">Int64</span></span>|  
|<span data-ttu-id="0b990-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-521">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-522">String</span><span class="sxs-lookup"><span data-stu-id="0b990-522">String</span></span>|  
|<span data-ttu-id="0b990-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-523">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-524">Guid</span></span>|  
|<span data-ttu-id="0b990-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-526">Int64</span></span>|  
|<span data-ttu-id="0b990-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0b990-527">COLLATION</span></span>|<span data-ttu-id="0b990-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-528">Int16</span></span>|  
|<span data-ttu-id="0b990-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0b990-529">CARDINALITY</span></span>|<span data-ttu-id="0b990-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0b990-530">Decimal</span></span>|  
|<span data-ttu-id="0b990-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="0b990-531">PAGES</span></span>|<span data-ttu-id="0b990-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-532">Int32</span></span>|  
|<span data-ttu-id="0b990-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b990-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0b990-534">String</span><span class="sxs-lookup"><span data-stu-id="0b990-534">String</span></span>|  
|<span data-ttu-id="0b990-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0b990-535">INTEGRATED</span></span>|<span data-ttu-id="0b990-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0b990-537">Dostawca programu Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="0b990-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="0b990-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje z określonego schematu, oprócz Typowe kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="0b990-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="0b990-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-539">Tables</span></span>  
  
-   <span data-ttu-id="0b990-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-540">Columns</span></span>  
  
-   <span data-ttu-id="0b990-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-541">Procedures</span></span>  
  
-   <span data-ttu-id="0b990-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="0b990-542">Views</span></span>  
  
-   <span data-ttu-id="0b990-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0b990-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="0b990-544">Tables</span></span>  
  
|<span data-ttu-id="0b990-545">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-545">ColumnName</span></span>|<span data-ttu-id="0b990-546">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-548">String</span><span class="sxs-lookup"><span data-stu-id="0b990-548">String</span></span>|  
|<span data-ttu-id="0b990-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-550">String</span><span class="sxs-lookup"><span data-stu-id="0b990-550">String</span></span>|  
|<span data-ttu-id="0b990-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-551">TABLE_NAME</span></span>|<span data-ttu-id="0b990-552">String</span><span class="sxs-lookup"><span data-stu-id="0b990-552">String</span></span>|  
|<span data-ttu-id="0b990-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-553">TABLE_TYPE</span></span>|<span data-ttu-id="0b990-554">String</span><span class="sxs-lookup"><span data-stu-id="0b990-554">String</span></span>|  
|<span data-ttu-id="0b990-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-555">TABLE_GUID</span></span>|<span data-ttu-id="0b990-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-556">Guid</span></span>|  
|<span data-ttu-id="0b990-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-557">DESCRIPTION</span></span>|<span data-ttu-id="0b990-558">String</span><span class="sxs-lookup"><span data-stu-id="0b990-558">String</span></span>|  
|<span data-ttu-id="0b990-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-559">TABLE_PROPID</span></span>|<span data-ttu-id="0b990-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-560">Int64</span></span>|  
|<span data-ttu-id="0b990-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-561">DATE_CREATED</span></span>|<span data-ttu-id="0b990-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-562">DateTime</span></span>|  
|<span data-ttu-id="0b990-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0b990-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-565">Columns</span></span>  
  
|<span data-ttu-id="0b990-566">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-566">ColumnName</span></span>|<span data-ttu-id="0b990-567">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-569">String</span><span class="sxs-lookup"><span data-stu-id="0b990-569">String</span></span>|  
|<span data-ttu-id="0b990-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-571">String</span><span class="sxs-lookup"><span data-stu-id="0b990-571">String</span></span>|  
|<span data-ttu-id="0b990-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-572">TABLE_NAME</span></span>|<span data-ttu-id="0b990-573">String</span><span class="sxs-lookup"><span data-stu-id="0b990-573">String</span></span>|  
|<span data-ttu-id="0b990-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-574">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-575">String</span><span class="sxs-lookup"><span data-stu-id="0b990-575">String</span></span>|  
|<span data-ttu-id="0b990-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-576">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-577">Guid</span></span>|  
|<span data-ttu-id="0b990-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-579">Int64</span></span>|  
|<span data-ttu-id="0b990-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-581">Int64</span></span>|  
|<span data-ttu-id="0b990-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0b990-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-583">Boolean</span></span>|  
|<span data-ttu-id="0b990-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0b990-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0b990-585">String</span><span class="sxs-lookup"><span data-stu-id="0b990-585">String</span></span>|  
|<span data-ttu-id="0b990-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0b990-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0b990-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-587">Int64</span></span>|  
|<span data-ttu-id="0b990-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-588">IS_NULLABLE</span></span>|<span data-ttu-id="0b990-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-589">Boolean</span></span>|  
|<span data-ttu-id="0b990-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-590">DATA_TYPE</span></span>|<span data-ttu-id="0b990-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-591">Int32</span></span>|  
|<span data-ttu-id="0b990-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-592">TYPE_GUID</span></span>|<span data-ttu-id="0b990-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-593">Guid</span></span>|  
|<span data-ttu-id="0b990-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0b990-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-595">Int64</span></span>|  
|<span data-ttu-id="0b990-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0b990-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0b990-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-597">Int64</span></span>|  
|<span data-ttu-id="0b990-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0b990-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-599">Int32</span></span>|  
|<span data-ttu-id="0b990-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0b990-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0b990-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-601">Int16</span></span>|  
|<span data-ttu-id="0b990-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0b990-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0b990-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-603">Int64</span></span>|  
|<span data-ttu-id="0b990-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0b990-605">String</span><span class="sxs-lookup"><span data-stu-id="0b990-605">String</span></span>|  
|<span data-ttu-id="0b990-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0b990-607">String</span><span class="sxs-lookup"><span data-stu-id="0b990-607">String</span></span>|  
|<span data-ttu-id="0b990-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0b990-609">String</span><span class="sxs-lookup"><span data-stu-id="0b990-609">String</span></span>|  
|<span data-ttu-id="0b990-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0b990-611">String</span><span class="sxs-lookup"><span data-stu-id="0b990-611">String</span></span>|  
|<span data-ttu-id="0b990-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0b990-613">String</span><span class="sxs-lookup"><span data-stu-id="0b990-613">String</span></span>|  
|<span data-ttu-id="0b990-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-614">COLLATION_NAME</span></span>|<span data-ttu-id="0b990-615">String</span><span class="sxs-lookup"><span data-stu-id="0b990-615">String</span></span>|  
|<span data-ttu-id="0b990-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0b990-617">String</span><span class="sxs-lookup"><span data-stu-id="0b990-617">String</span></span>|  
|<span data-ttu-id="0b990-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0b990-619">String</span><span class="sxs-lookup"><span data-stu-id="0b990-619">String</span></span>|  
|<span data-ttu-id="0b990-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0b990-621">String</span><span class="sxs-lookup"><span data-stu-id="0b990-621">String</span></span>|  
|<span data-ttu-id="0b990-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-622">DESCRIPTION</span></span>|<span data-ttu-id="0b990-623">String</span><span class="sxs-lookup"><span data-stu-id="0b990-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0b990-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b990-624">Procedures</span></span>  
  
|<span data-ttu-id="0b990-625">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-625">ColumnName</span></span>|<span data-ttu-id="0b990-626">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0b990-628">String</span><span class="sxs-lookup"><span data-stu-id="0b990-628">String</span></span>|  
|<span data-ttu-id="0b990-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0b990-630">String</span><span class="sxs-lookup"><span data-stu-id="0b990-630">String</span></span>|  
|<span data-ttu-id="0b990-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0b990-632">String</span><span class="sxs-lookup"><span data-stu-id="0b990-632">String</span></span>|  
|<span data-ttu-id="0b990-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0b990-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0b990-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-634">Int16</span></span>|  
|<span data-ttu-id="0b990-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b990-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0b990-636">String</span><span class="sxs-lookup"><span data-stu-id="0b990-636">String</span></span>|  
|<span data-ttu-id="0b990-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-637">DESCRIPTION</span></span>|<span data-ttu-id="0b990-638">String</span><span class="sxs-lookup"><span data-stu-id="0b990-638">String</span></span>|  
|<span data-ttu-id="0b990-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-639">DATE_CREATED</span></span>|<span data-ttu-id="0b990-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-640">DateTime</span></span>|  
|<span data-ttu-id="0b990-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0b990-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="0b990-643">Views</span></span>  
  
|<span data-ttu-id="0b990-644">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-644">ColumnName</span></span>|<span data-ttu-id="0b990-645">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-647">String</span><span class="sxs-lookup"><span data-stu-id="0b990-647">String</span></span>|  
|<span data-ttu-id="0b990-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-649">String</span><span class="sxs-lookup"><span data-stu-id="0b990-649">String</span></span>|  
|<span data-ttu-id="0b990-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-650">TABLE_NAME</span></span>|<span data-ttu-id="0b990-651">String</span><span class="sxs-lookup"><span data-stu-id="0b990-651">String</span></span>|  
|<span data-ttu-id="0b990-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0b990-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0b990-653">String</span><span class="sxs-lookup"><span data-stu-id="0b990-653">String</span></span>|  
|<span data-ttu-id="0b990-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0b990-654">CHECK_OPTION</span></span>|<span data-ttu-id="0b990-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-655">Boolean</span></span>|  
|<span data-ttu-id="0b990-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0b990-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0b990-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-657">Boolean</span></span>|  
|<span data-ttu-id="0b990-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="0b990-658">DESCRIPTION</span></span>|<span data-ttu-id="0b990-659">String</span><span class="sxs-lookup"><span data-stu-id="0b990-659">String</span></span>|  
|<span data-ttu-id="0b990-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0b990-660">DATE_CREATED</span></span>|<span data-ttu-id="0b990-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-661">DateTime</span></span>|  
|<span data-ttu-id="0b990-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0b990-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0b990-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="0b990-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0b990-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="0b990-664">Indexes</span></span>  
  
|<span data-ttu-id="0b990-665">NazwaKolumny</span><span class="sxs-lookup"><span data-stu-id="0b990-665">ColumnName</span></span>|<span data-ttu-id="0b990-666">Typ danych</span><span class="sxs-lookup"><span data-stu-id="0b990-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0b990-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0b990-668">String</span><span class="sxs-lookup"><span data-stu-id="0b990-668">String</span></span>|  
|<span data-ttu-id="0b990-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0b990-670">String</span><span class="sxs-lookup"><span data-stu-id="0b990-670">String</span></span>|  
|<span data-ttu-id="0b990-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-671">TABLE_NAME</span></span>|<span data-ttu-id="0b990-672">String</span><span class="sxs-lookup"><span data-stu-id="0b990-672">String</span></span>|  
|<span data-ttu-id="0b990-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0b990-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0b990-674">String</span><span class="sxs-lookup"><span data-stu-id="0b990-674">String</span></span>|  
|<span data-ttu-id="0b990-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0b990-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0b990-676">String</span><span class="sxs-lookup"><span data-stu-id="0b990-676">String</span></span>|  
|<span data-ttu-id="0b990-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-677">INDEX_NAME</span></span>|<span data-ttu-id="0b990-678">String</span><span class="sxs-lookup"><span data-stu-id="0b990-678">String</span></span>|  
|<span data-ttu-id="0b990-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0b990-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0b990-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-680">Boolean</span></span>|  
|<span data-ttu-id="0b990-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0b990-681">UNIQUE</span></span>|<span data-ttu-id="0b990-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-682">Boolean</span></span>|  
|<span data-ttu-id="0b990-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0b990-683">CLUSTERED</span></span>|<span data-ttu-id="0b990-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-684">Boolean</span></span>|  
|<span data-ttu-id="0b990-685">TYP</span><span class="sxs-lookup"><span data-stu-id="0b990-685">TYPE</span></span>|<span data-ttu-id="0b990-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-686">Int32</span></span>|  
|<span data-ttu-id="0b990-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0b990-687">FILL_FACTOR</span></span>|<span data-ttu-id="0b990-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-688">Int32</span></span>|  
|<span data-ttu-id="0b990-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0b990-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0b990-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-690">Int32</span></span>|  
|<span data-ttu-id="0b990-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="0b990-691">NULLS</span></span>|<span data-ttu-id="0b990-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-692">Int32</span></span>|  
|<span data-ttu-id="0b990-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0b990-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0b990-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-694">Boolean</span></span>|  
|<span data-ttu-id="0b990-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0b990-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0b990-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-696">Boolean</span></span>|  
|<span data-ttu-id="0b990-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0b990-697">NULL_COLLATION</span></span>|<span data-ttu-id="0b990-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-698">Int32</span></span>|  
|<span data-ttu-id="0b990-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0b990-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0b990-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-700">Int64</span></span>|  
|<span data-ttu-id="0b990-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0b990-701">COLUMN_NAME</span></span>|<span data-ttu-id="0b990-702">String</span><span class="sxs-lookup"><span data-stu-id="0b990-702">String</span></span>|  
|<span data-ttu-id="0b990-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-703">COLUMN_GUID</span></span>|<span data-ttu-id="0b990-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="0b990-704">Guid</span></span>|  
|<span data-ttu-id="0b990-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0b990-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0b990-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0b990-706">Int64</span></span>|  
|<span data-ttu-id="0b990-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="0b990-707">COLLATION</span></span>|<span data-ttu-id="0b990-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0b990-708">Int16</span></span>|  
|<span data-ttu-id="0b990-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="0b990-709">CARDINALITY</span></span>|<span data-ttu-id="0b990-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="0b990-710">Decimal</span></span>|  
|<span data-ttu-id="0b990-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="0b990-711">PAGES</span></span>|<span data-ttu-id="0b990-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0b990-712">Int32</span></span>|  
|<span data-ttu-id="0b990-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0b990-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0b990-714">String</span><span class="sxs-lookup"><span data-stu-id="0b990-714">String</span></span>|  
|<span data-ttu-id="0b990-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="0b990-715">INTEGRATED</span></span>|<span data-ttu-id="0b990-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="0b990-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b990-717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b990-717">See Also</span></span>  
 [<span data-ttu-id="0b990-718">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="0b990-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
