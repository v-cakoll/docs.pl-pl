---
title: Kolekcje schematów OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f1cb5e1fe967088b44fa4045dfe50c1c57d963eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766936"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="117d9-102">Kolekcje schematów OLE DB</span><span class="sxs-lookup"><span data-stu-id="117d9-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="117d9-103">W tej sekcji omówiono obsługi kolekcji schematu dla dostawcy OLE DB dla programu Microsoft SQL Server, Oracle i Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="117d9-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="117d9-104">Dostawca programu Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="117d9-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="117d9-105">Sterownik firmy Microsoft SQL Server OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="117d9-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="117d9-106">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-106">Tables</span></span>  
  
-   <span data-ttu-id="117d9-107">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-107">Columns</span></span>  
  
-   <span data-ttu-id="117d9-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-108">Procedures</span></span>  
  
-   <span data-ttu-id="117d9-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="117d9-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="117d9-110">Katalogu</span><span class="sxs-lookup"><span data-stu-id="117d9-110">Catalog</span></span>  
  
-   <span data-ttu-id="117d9-111">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="117d9-112">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-112">Tables</span></span>  
  
|<span data-ttu-id="117d9-113">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-113">ColumnName</span></span>|<span data-ttu-id="117d9-114">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-115">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-116">String</span><span class="sxs-lookup"><span data-stu-id="117d9-116">String</span></span>|  
|<span data-ttu-id="117d9-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-118">String</span><span class="sxs-lookup"><span data-stu-id="117d9-118">String</span></span>|  
|<span data-ttu-id="117d9-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-119">TABLE_NAME</span></span>|<span data-ttu-id="117d9-120">String</span><span class="sxs-lookup"><span data-stu-id="117d9-120">String</span></span>|  
|<span data-ttu-id="117d9-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-121">TABLE_TYPE</span></span>|<span data-ttu-id="117d9-122">String</span><span class="sxs-lookup"><span data-stu-id="117d9-122">String</span></span>|  
|<span data-ttu-id="117d9-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-123">TABLE_GUID</span></span>|<span data-ttu-id="117d9-124">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-124">Guid</span></span>|  
|<span data-ttu-id="117d9-125">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-125">DESCRIPTION</span></span>|<span data-ttu-id="117d9-126">String</span><span class="sxs-lookup"><span data-stu-id="117d9-126">String</span></span>|  
|<span data-ttu-id="117d9-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-127">TABLE_PROPID</span></span>|<span data-ttu-id="117d9-128">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-128">Int64</span></span>|  
|<span data-ttu-id="117d9-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-129">DATE_CREATED</span></span>|<span data-ttu-id="117d9-130">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-130">DateTime</span></span>|  
|<span data-ttu-id="117d9-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-131">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-132">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="117d9-133">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-133">Columns</span></span>  
  
|<span data-ttu-id="117d9-134">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-134">ColumnName</span></span>|<span data-ttu-id="117d9-135">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-136">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-137">String</span><span class="sxs-lookup"><span data-stu-id="117d9-137">String</span></span>|  
|<span data-ttu-id="117d9-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-139">String</span><span class="sxs-lookup"><span data-stu-id="117d9-139">String</span></span>|  
|<span data-ttu-id="117d9-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-140">TABLE_NAME</span></span>|<span data-ttu-id="117d9-141">String</span><span class="sxs-lookup"><span data-stu-id="117d9-141">String</span></span>|  
|<span data-ttu-id="117d9-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-142">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-143">String</span><span class="sxs-lookup"><span data-stu-id="117d9-143">String</span></span>|  
|<span data-ttu-id="117d9-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-144">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-145">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-145">Guid</span></span>|  
|<span data-ttu-id="117d9-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-146">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-147">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-147">Int64</span></span>|  
|<span data-ttu-id="117d9-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-149">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-149">Int64</span></span>|  
|<span data-ttu-id="117d9-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="117d9-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-151">Boolean</span></span>|  
|<span data-ttu-id="117d9-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="117d9-153">String</span><span class="sxs-lookup"><span data-stu-id="117d9-153">String</span></span>|  
|<span data-ttu-id="117d9-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="117d9-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="117d9-155">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-155">Int64</span></span>|  
|<span data-ttu-id="117d9-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-156">IS_NULLABLE</span></span>|<span data-ttu-id="117d9-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-157">Boolean</span></span>|  
|<span data-ttu-id="117d9-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-158">DATA_TYPE</span></span>|<span data-ttu-id="117d9-159">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-159">Int32</span></span>|  
|<span data-ttu-id="117d9-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-160">TYPE_GUID</span></span>|<span data-ttu-id="117d9-161">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-161">Guid</span></span>|  
|<span data-ttu-id="117d9-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="117d9-163">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-163">Int64</span></span>|  
|<span data-ttu-id="117d9-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="117d9-165">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-165">Int64</span></span>|  
|<span data-ttu-id="117d9-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="117d9-167">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-167">Int32</span></span>|  
|<span data-ttu-id="117d9-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="117d9-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="117d9-169">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-169">Int16</span></span>|  
|<span data-ttu-id="117d9-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="117d9-171">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-171">Int64</span></span>|  
|<span data-ttu-id="117d9-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="117d9-173">String</span><span class="sxs-lookup"><span data-stu-id="117d9-173">String</span></span>|  
|<span data-ttu-id="117d9-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="117d9-175">String</span><span class="sxs-lookup"><span data-stu-id="117d9-175">String</span></span>|  
|<span data-ttu-id="117d9-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="117d9-177">String</span><span class="sxs-lookup"><span data-stu-id="117d9-177">String</span></span>|  
|<span data-ttu-id="117d9-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="117d9-179">String</span><span class="sxs-lookup"><span data-stu-id="117d9-179">String</span></span>|  
|<span data-ttu-id="117d9-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="117d9-181">String</span><span class="sxs-lookup"><span data-stu-id="117d9-181">String</span></span>|  
|<span data-ttu-id="117d9-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-182">COLLATION_NAME</span></span>|<span data-ttu-id="117d9-183">String</span><span class="sxs-lookup"><span data-stu-id="117d9-183">String</span></span>|  
|<span data-ttu-id="117d9-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="117d9-185">String</span><span class="sxs-lookup"><span data-stu-id="117d9-185">String</span></span>|  
|<span data-ttu-id="117d9-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="117d9-187">String</span><span class="sxs-lookup"><span data-stu-id="117d9-187">String</span></span>|  
|<span data-ttu-id="117d9-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-188">DOMAIN_NAME</span></span>|<span data-ttu-id="117d9-189">String</span><span class="sxs-lookup"><span data-stu-id="117d9-189">String</span></span>|  
|<span data-ttu-id="117d9-190">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-190">DESCRIPTION</span></span>|<span data-ttu-id="117d9-191">String</span><span class="sxs-lookup"><span data-stu-id="117d9-191">String</span></span>|  
|<span data-ttu-id="117d9-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="117d9-192">COLUMN_LCID</span></span>|<span data-ttu-id="117d9-193">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-193">Int32</span></span>|  
|<span data-ttu-id="117d9-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="117d9-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="117d9-195">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-195">Int32</span></span>|  
|<span data-ttu-id="117d9-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="117d9-196">COLUMN_SORTID</span></span>|<span data-ttu-id="117d9-197">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-197">Int32</span></span>|  
|<span data-ttu-id="117d9-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="117d9-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="117d9-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="117d9-199">Byte[]</span></span>|  
|<span data-ttu-id="117d9-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="117d9-200">IS_COMPUTED</span></span>|<span data-ttu-id="117d9-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="117d9-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-202">Procedures</span></span>  
  
|<span data-ttu-id="117d9-203">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-203">ColumnName</span></span>|<span data-ttu-id="117d9-204">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="117d9-206">String</span><span class="sxs-lookup"><span data-stu-id="117d9-206">String</span></span>|  
|<span data-ttu-id="117d9-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="117d9-208">String</span><span class="sxs-lookup"><span data-stu-id="117d9-208">String</span></span>|  
|<span data-ttu-id="117d9-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="117d9-210">String</span><span class="sxs-lookup"><span data-stu-id="117d9-210">String</span></span>|  
|<span data-ttu-id="117d9-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="117d9-212">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-212">Int16</span></span>|  
|<span data-ttu-id="117d9-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="117d9-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="117d9-214">String</span><span class="sxs-lookup"><span data-stu-id="117d9-214">String</span></span>|  
|<span data-ttu-id="117d9-215">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-215">DESCRIPTION</span></span>|<span data-ttu-id="117d9-216">String</span><span class="sxs-lookup"><span data-stu-id="117d9-216">String</span></span>|  
|<span data-ttu-id="117d9-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-217">DATE_CREATED</span></span>|<span data-ttu-id="117d9-218">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-218">DateTime</span></span>|  
|<span data-ttu-id="117d9-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-219">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-220">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="117d9-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="117d9-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="117d9-222">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-222">ColumnName</span></span>|<span data-ttu-id="117d9-223">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="117d9-225">String</span><span class="sxs-lookup"><span data-stu-id="117d9-225">String</span></span>|  
|<span data-ttu-id="117d9-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="117d9-227">String</span><span class="sxs-lookup"><span data-stu-id="117d9-227">String</span></span>|  
|<span data-ttu-id="117d9-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="117d9-229">String</span><span class="sxs-lookup"><span data-stu-id="117d9-229">String</span></span>|  
|<span data-ttu-id="117d9-230">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="117d9-230">PARAMETER_NAME</span></span>|<span data-ttu-id="117d9-231">String</span><span class="sxs-lookup"><span data-stu-id="117d9-231">String</span></span>|  
|<span data-ttu-id="117d9-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-233">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-233">Int32</span></span>|  
|<span data-ttu-id="117d9-234">TYP_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="117d9-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="117d9-235">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-235">Int32</span></span>|  
|<span data-ttu-id="117d9-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="117d9-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-237">Boolean</span></span>|  
|<span data-ttu-id="117d9-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="117d9-239">String</span><span class="sxs-lookup"><span data-stu-id="117d9-239">String</span></span>|  
|<span data-ttu-id="117d9-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-240">IS_NULLABLE</span></span>|<span data-ttu-id="117d9-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-241">Boolean</span></span>|  
|<span data-ttu-id="117d9-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-242">DATA_TYPE</span></span>|<span data-ttu-id="117d9-243">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-243">Int32</span></span>|  
|<span data-ttu-id="117d9-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="117d9-245">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-245">Int64</span></span>|  
|<span data-ttu-id="117d9-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="117d9-247">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-247">Int64</span></span>|  
|<span data-ttu-id="117d9-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="117d9-249">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-249">Int32</span></span>|  
|<span data-ttu-id="117d9-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="117d9-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="117d9-251">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-251">Int16</span></span>|  
|<span data-ttu-id="117d9-252">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-252">DESCRIPTION</span></span>|<span data-ttu-id="117d9-253">String</span><span class="sxs-lookup"><span data-stu-id="117d9-253">String</span></span>|  
|<span data-ttu-id="117d9-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-254">TYPE_NAME</span></span>|<span data-ttu-id="117d9-255">String</span><span class="sxs-lookup"><span data-stu-id="117d9-255">String</span></span>|  
|<span data-ttu-id="117d9-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="117d9-257">String</span><span class="sxs-lookup"><span data-stu-id="117d9-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="117d9-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="117d9-258">Catalog</span></span>  
  
|<span data-ttu-id="117d9-259">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-259">ColumnName</span></span>|<span data-ttu-id="117d9-260">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-261">CATALOG_NAME</span></span>|<span data-ttu-id="117d9-262">String</span><span class="sxs-lookup"><span data-stu-id="117d9-262">String</span></span>|  
|<span data-ttu-id="117d9-263">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-263">DESCRIPTION</span></span>|<span data-ttu-id="117d9-264">String</span><span class="sxs-lookup"><span data-stu-id="117d9-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="117d9-265">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-265">Indexes</span></span>  
  
|<span data-ttu-id="117d9-266">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-266">ColumnName</span></span>|<span data-ttu-id="117d9-267">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-268">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-269">String</span><span class="sxs-lookup"><span data-stu-id="117d9-269">String</span></span>|  
|<span data-ttu-id="117d9-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-271">String</span><span class="sxs-lookup"><span data-stu-id="117d9-271">String</span></span>|  
|<span data-ttu-id="117d9-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-272">TABLE_NAME</span></span>|<span data-ttu-id="117d9-273">String</span><span class="sxs-lookup"><span data-stu-id="117d9-273">String</span></span>|  
|<span data-ttu-id="117d9-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-274">INDEX_CATALOG</span></span>|<span data-ttu-id="117d9-275">String</span><span class="sxs-lookup"><span data-stu-id="117d9-275">String</span></span>|  
|<span data-ttu-id="117d9-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="117d9-277">String</span><span class="sxs-lookup"><span data-stu-id="117d9-277">String</span></span>|  
|<span data-ttu-id="117d9-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-278">INDEX_NAME</span></span>|<span data-ttu-id="117d9-279">String</span><span class="sxs-lookup"><span data-stu-id="117d9-279">String</span></span>|  
|<span data-ttu-id="117d9-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="117d9-280">PRIMARY_KEY</span></span>|<span data-ttu-id="117d9-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-281">Boolean</span></span>|  
|<span data-ttu-id="117d9-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="117d9-282">UNIQUE</span></span>|<span data-ttu-id="117d9-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-283">Boolean</span></span>|  
|<span data-ttu-id="117d9-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="117d9-284">CLUSTERED</span></span>|<span data-ttu-id="117d9-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-285">Boolean</span></span>|  
|<span data-ttu-id="117d9-286">TYP</span><span class="sxs-lookup"><span data-stu-id="117d9-286">TYPE</span></span>|<span data-ttu-id="117d9-287">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-287">Int32</span></span>|  
|<span data-ttu-id="117d9-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="117d9-288">FILL_FACTOR</span></span>|<span data-ttu-id="117d9-289">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-289">Int32</span></span>|  
|<span data-ttu-id="117d9-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="117d9-290">INITIAL_SIZE</span></span>|<span data-ttu-id="117d9-291">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-291">Int32</span></span>|  
|<span data-ttu-id="117d9-292">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="117d9-292">NULLS</span></span>|<span data-ttu-id="117d9-293">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-293">Int32</span></span>|  
|<span data-ttu-id="117d9-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="117d9-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="117d9-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-295">Boolean</span></span>|  
|<span data-ttu-id="117d9-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="117d9-296">AUTO_UPDATE</span></span>|<span data-ttu-id="117d9-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-297">Boolean</span></span>|  
|<span data-ttu-id="117d9-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="117d9-298">NULL_COLLATION</span></span>|<span data-ttu-id="117d9-299">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-299">Int32</span></span>|  
|<span data-ttu-id="117d9-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-301">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-301">Int64</span></span>|  
|<span data-ttu-id="117d9-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-302">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-303">String</span><span class="sxs-lookup"><span data-stu-id="117d9-303">String</span></span>|  
|<span data-ttu-id="117d9-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-304">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-305">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-305">Guid</span></span>|  
|<span data-ttu-id="117d9-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-306">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-307">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-307">Int64</span></span>|  
|<span data-ttu-id="117d9-308">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="117d9-308">COLLATION</span></span>|<span data-ttu-id="117d9-309">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-309">Int16</span></span>|  
|<span data-ttu-id="117d9-310">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="117d9-310">CARDINALITY</span></span>|<span data-ttu-id="117d9-311">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="117d9-311">Decimal</span></span>|  
|<span data-ttu-id="117d9-312">STRONY</span><span class="sxs-lookup"><span data-stu-id="117d9-312">PAGES</span></span>|<span data-ttu-id="117d9-313">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-313">Int32</span></span>|  
|<span data-ttu-id="117d9-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="117d9-314">FILTER_CONDITION</span></span>|<span data-ttu-id="117d9-315">String</span><span class="sxs-lookup"><span data-stu-id="117d9-315">String</span></span>|  
|<span data-ttu-id="117d9-316">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="117d9-316">INTEGRATED</span></span>|<span data-ttu-id="117d9-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="117d9-318">Dostawca programu Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="117d9-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="117d9-319">Sterownik firmy Microsoft Oracle OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="117d9-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="117d9-320">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-320">Tables</span></span>  
  
-   <span data-ttu-id="117d9-321">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-321">Columns</span></span>  
  
-   <span data-ttu-id="117d9-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-322">Procedures</span></span>  
  
-   <span data-ttu-id="117d9-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="117d9-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="117d9-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="117d9-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="117d9-325">Widoki</span><span class="sxs-lookup"><span data-stu-id="117d9-325">Views</span></span>  
  
-   <span data-ttu-id="117d9-326">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="117d9-327">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-327">Tables</span></span>  
  
|<span data-ttu-id="117d9-328">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-328">ColumnName</span></span>|<span data-ttu-id="117d9-329">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-330">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-331">String</span><span class="sxs-lookup"><span data-stu-id="117d9-331">String</span></span>|  
|<span data-ttu-id="117d9-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-333">String</span><span class="sxs-lookup"><span data-stu-id="117d9-333">String</span></span>|  
|<span data-ttu-id="117d9-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-334">TABLE_NAME</span></span>|<span data-ttu-id="117d9-335">String</span><span class="sxs-lookup"><span data-stu-id="117d9-335">String</span></span>|  
|<span data-ttu-id="117d9-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-336">TABLE_TYPE</span></span>|<span data-ttu-id="117d9-337">String</span><span class="sxs-lookup"><span data-stu-id="117d9-337">String</span></span>|  
|<span data-ttu-id="117d9-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-338">TABLE_GUID</span></span>|<span data-ttu-id="117d9-339">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-339">Guid</span></span>|  
|<span data-ttu-id="117d9-340">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-340">DESCRIPTION</span></span>|<span data-ttu-id="117d9-341">String</span><span class="sxs-lookup"><span data-stu-id="117d9-341">String</span></span>|  
|<span data-ttu-id="117d9-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-342">TABLE_PROPID</span></span>|<span data-ttu-id="117d9-343">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-343">Int64</span></span>|  
|<span data-ttu-id="117d9-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-344">DATE_CREATED</span></span>|<span data-ttu-id="117d9-345">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-345">DateTime</span></span>|  
|<span data-ttu-id="117d9-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-346">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-347">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="117d9-348">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-348">Columns</span></span>  
  
|<span data-ttu-id="117d9-349">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-349">ColumnName</span></span>|<span data-ttu-id="117d9-350">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-351">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-352">String</span><span class="sxs-lookup"><span data-stu-id="117d9-352">String</span></span>|  
|<span data-ttu-id="117d9-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-354">String</span><span class="sxs-lookup"><span data-stu-id="117d9-354">String</span></span>|  
|<span data-ttu-id="117d9-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-355">TABLE_NAME</span></span>|<span data-ttu-id="117d9-356">String</span><span class="sxs-lookup"><span data-stu-id="117d9-356">String</span></span>|  
|<span data-ttu-id="117d9-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-357">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-358">String</span><span class="sxs-lookup"><span data-stu-id="117d9-358">String</span></span>|  
|<span data-ttu-id="117d9-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-359">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-360">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-360">Guid</span></span>|  
|<span data-ttu-id="117d9-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-361">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-362">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-362">Int64</span></span>|  
|<span data-ttu-id="117d9-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-364">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-364">Int64</span></span>|  
|<span data-ttu-id="117d9-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="117d9-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-366">Boolean</span></span>|  
|<span data-ttu-id="117d9-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="117d9-368">String</span><span class="sxs-lookup"><span data-stu-id="117d9-368">String</span></span>|  
|<span data-ttu-id="117d9-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="117d9-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="117d9-370">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-370">Int64</span></span>|  
|<span data-ttu-id="117d9-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-371">IS_NULLABLE</span></span>|<span data-ttu-id="117d9-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-372">Boolean</span></span>|  
|<span data-ttu-id="117d9-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-373">DATA_TYPE</span></span>|<span data-ttu-id="117d9-374">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-374">Int32</span></span>|  
|<span data-ttu-id="117d9-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-375">TYPE_GUID</span></span>|<span data-ttu-id="117d9-376">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-376">Guid</span></span>|  
|<span data-ttu-id="117d9-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="117d9-378">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-378">Int64</span></span>|  
|<span data-ttu-id="117d9-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="117d9-380">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-380">Int64</span></span>|  
|<span data-ttu-id="117d9-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="117d9-382">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-382">Int32</span></span>|  
|<span data-ttu-id="117d9-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="117d9-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="117d9-384">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-384">Int16</span></span>|  
|<span data-ttu-id="117d9-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="117d9-386">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-386">Int64</span></span>|  
|<span data-ttu-id="117d9-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="117d9-388">String</span><span class="sxs-lookup"><span data-stu-id="117d9-388">String</span></span>|  
|<span data-ttu-id="117d9-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="117d9-390">String</span><span class="sxs-lookup"><span data-stu-id="117d9-390">String</span></span>|  
|<span data-ttu-id="117d9-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="117d9-392">String</span><span class="sxs-lookup"><span data-stu-id="117d9-392">String</span></span>|  
|<span data-ttu-id="117d9-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="117d9-394">String</span><span class="sxs-lookup"><span data-stu-id="117d9-394">String</span></span>|  
|<span data-ttu-id="117d9-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="117d9-396">String</span><span class="sxs-lookup"><span data-stu-id="117d9-396">String</span></span>|  
|<span data-ttu-id="117d9-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-397">COLLATION_NAME</span></span>|<span data-ttu-id="117d9-398">String</span><span class="sxs-lookup"><span data-stu-id="117d9-398">String</span></span>|  
|<span data-ttu-id="117d9-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="117d9-400">String</span><span class="sxs-lookup"><span data-stu-id="117d9-400">String</span></span>|  
|<span data-ttu-id="117d9-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="117d9-402">String</span><span class="sxs-lookup"><span data-stu-id="117d9-402">String</span></span>|  
|<span data-ttu-id="117d9-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-403">DOMAIN_NAME</span></span>|<span data-ttu-id="117d9-404">String</span><span class="sxs-lookup"><span data-stu-id="117d9-404">String</span></span>|  
|<span data-ttu-id="117d9-405">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-405">DESCRIPTION</span></span>|<span data-ttu-id="117d9-406">String</span><span class="sxs-lookup"><span data-stu-id="117d9-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="117d9-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-407">Procedures</span></span>  
  
|<span data-ttu-id="117d9-408">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-408">ColumnName</span></span>|<span data-ttu-id="117d9-409">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="117d9-411">String</span><span class="sxs-lookup"><span data-stu-id="117d9-411">String</span></span>|  
|<span data-ttu-id="117d9-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="117d9-413">String</span><span class="sxs-lookup"><span data-stu-id="117d9-413">String</span></span>|  
|<span data-ttu-id="117d9-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="117d9-415">String</span><span class="sxs-lookup"><span data-stu-id="117d9-415">String</span></span>|  
|<span data-ttu-id="117d9-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="117d9-417">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-417">Int16</span></span>|  
|<span data-ttu-id="117d9-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="117d9-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="117d9-419">String</span><span class="sxs-lookup"><span data-stu-id="117d9-419">String</span></span>|  
|<span data-ttu-id="117d9-420">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-420">DESCRIPTION</span></span>|<span data-ttu-id="117d9-421">String</span><span class="sxs-lookup"><span data-stu-id="117d9-421">String</span></span>|  
|<span data-ttu-id="117d9-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-422">DATE_CREATED</span></span>|<span data-ttu-id="117d9-423">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-423">DateTime</span></span>|  
|<span data-ttu-id="117d9-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-424">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-425">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="117d9-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="117d9-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="117d9-427">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-427">ColumnName</span></span>|<span data-ttu-id="117d9-428">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="117d9-430">String</span><span class="sxs-lookup"><span data-stu-id="117d9-430">String</span></span>|  
|<span data-ttu-id="117d9-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="117d9-432">String</span><span class="sxs-lookup"><span data-stu-id="117d9-432">String</span></span>|  
|<span data-ttu-id="117d9-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="117d9-434">String</span><span class="sxs-lookup"><span data-stu-id="117d9-434">String</span></span>|  
|<span data-ttu-id="117d9-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-435">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-436">String</span><span class="sxs-lookup"><span data-stu-id="117d9-436">String</span></span>|  
|<span data-ttu-id="117d9-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-437">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-438">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-438">Guid</span></span>|  
|<span data-ttu-id="117d9-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-439">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-440">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-440">Int64</span></span>|  
|<span data-ttu-id="117d9-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="117d9-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="117d9-442">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-442">Int64</span></span>|  
|<span data-ttu-id="117d9-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-444">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-444">Int64</span></span>|  
|<span data-ttu-id="117d9-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-445">IS_NULLABLE</span></span>|<span data-ttu-id="117d9-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-446">Boolean</span></span>|  
|<span data-ttu-id="117d9-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-447">DATA_TYPE</span></span>|<span data-ttu-id="117d9-448">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-448">Int32</span></span>|  
|<span data-ttu-id="117d9-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-449">TYPE_GUID</span></span>|<span data-ttu-id="117d9-450">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-450">Guid</span></span>|  
|<span data-ttu-id="117d9-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="117d9-452">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-452">Int64</span></span>|  
|<span data-ttu-id="117d9-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="117d9-454">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-454">Int64</span></span>|  
|<span data-ttu-id="117d9-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="117d9-456">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-456">Int32</span></span>|  
|<span data-ttu-id="117d9-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="117d9-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="117d9-458">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-458">Int16</span></span>|  
|<span data-ttu-id="117d9-459">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-459">DESCRIPTION</span></span>|<span data-ttu-id="117d9-460">String</span><span class="sxs-lookup"><span data-stu-id="117d9-460">String</span></span>|  
|<span data-ttu-id="117d9-461">PRZECIĄŻENIA</span><span class="sxs-lookup"><span data-stu-id="117d9-461">OVERLOAD</span></span>|<span data-ttu-id="117d9-462">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="117d9-463">Widoki</span><span class="sxs-lookup"><span data-stu-id="117d9-463">Views</span></span>  
  
|<span data-ttu-id="117d9-464">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-464">ColumnName</span></span>|<span data-ttu-id="117d9-465">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-466">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-467">String</span><span class="sxs-lookup"><span data-stu-id="117d9-467">String</span></span>|  
|<span data-ttu-id="117d9-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-469">String</span><span class="sxs-lookup"><span data-stu-id="117d9-469">String</span></span>|  
|<span data-ttu-id="117d9-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-470">TABLE_NAME</span></span>|<span data-ttu-id="117d9-471">String</span><span class="sxs-lookup"><span data-stu-id="117d9-471">String</span></span>|  
|<span data-ttu-id="117d9-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="117d9-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="117d9-473">String</span><span class="sxs-lookup"><span data-stu-id="117d9-473">String</span></span>|  
|<span data-ttu-id="117d9-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="117d9-474">CHECK_OPTION</span></span>|<span data-ttu-id="117d9-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-475">Boolean</span></span>|  
|<span data-ttu-id="117d9-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-476">IS_UPDATABLE</span></span>|<span data-ttu-id="117d9-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-477">Boolean</span></span>|  
|<span data-ttu-id="117d9-478">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-478">DESCRIPTION</span></span>|<span data-ttu-id="117d9-479">String</span><span class="sxs-lookup"><span data-stu-id="117d9-479">String</span></span>|  
|<span data-ttu-id="117d9-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-480">DATE_CREATED</span></span>|<span data-ttu-id="117d9-481">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-481">DateTime</span></span>|  
|<span data-ttu-id="117d9-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-482">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-483">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="117d9-484">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-484">Indexes</span></span>  
  
|<span data-ttu-id="117d9-485">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-485">ColumnName</span></span>|<span data-ttu-id="117d9-486">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-487">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-488">String</span><span class="sxs-lookup"><span data-stu-id="117d9-488">String</span></span>|  
|<span data-ttu-id="117d9-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-490">String</span><span class="sxs-lookup"><span data-stu-id="117d9-490">String</span></span>|  
|<span data-ttu-id="117d9-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-491">TABLE_NAME</span></span>|<span data-ttu-id="117d9-492">String</span><span class="sxs-lookup"><span data-stu-id="117d9-492">String</span></span>|  
|<span data-ttu-id="117d9-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-493">INDEX_CATALOG</span></span>|<span data-ttu-id="117d9-494">String</span><span class="sxs-lookup"><span data-stu-id="117d9-494">String</span></span>|  
|<span data-ttu-id="117d9-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="117d9-496">String</span><span class="sxs-lookup"><span data-stu-id="117d9-496">String</span></span>|  
|<span data-ttu-id="117d9-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-497">INDEX_NAME</span></span>|<span data-ttu-id="117d9-498">String</span><span class="sxs-lookup"><span data-stu-id="117d9-498">String</span></span>|  
|<span data-ttu-id="117d9-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="117d9-499">PRIMARY_KEY</span></span>|<span data-ttu-id="117d9-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-500">Boolean</span></span>|  
|<span data-ttu-id="117d9-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="117d9-501">UNIQUE</span></span>|<span data-ttu-id="117d9-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-502">Boolean</span></span>|  
|<span data-ttu-id="117d9-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="117d9-503">CLUSTERED</span></span>|<span data-ttu-id="117d9-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-504">Boolean</span></span>|  
|<span data-ttu-id="117d9-505">TYP</span><span class="sxs-lookup"><span data-stu-id="117d9-505">TYPE</span></span>|<span data-ttu-id="117d9-506">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-506">Int32</span></span>|  
|<span data-ttu-id="117d9-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="117d9-507">FILL_FACTOR</span></span>|<span data-ttu-id="117d9-508">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-508">Int32</span></span>|  
|<span data-ttu-id="117d9-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="117d9-509">INITIAL_SIZE</span></span>|<span data-ttu-id="117d9-510">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-510">Int32</span></span>|  
|<span data-ttu-id="117d9-511">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="117d9-511">NULLS</span></span>|<span data-ttu-id="117d9-512">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-512">Int32</span></span>|  
|<span data-ttu-id="117d9-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="117d9-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="117d9-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-514">Boolean</span></span>|  
|<span data-ttu-id="117d9-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="117d9-515">AUTO_UPDATE</span></span>|<span data-ttu-id="117d9-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-516">Boolean</span></span>|  
|<span data-ttu-id="117d9-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="117d9-517">NULL_COLLATION</span></span>|<span data-ttu-id="117d9-518">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-518">Int32</span></span>|  
|<span data-ttu-id="117d9-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-520">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-520">Int64</span></span>|  
|<span data-ttu-id="117d9-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-521">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-522">String</span><span class="sxs-lookup"><span data-stu-id="117d9-522">String</span></span>|  
|<span data-ttu-id="117d9-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-523">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-524">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-524">Guid</span></span>|  
|<span data-ttu-id="117d9-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-525">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-526">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-526">Int64</span></span>|  
|<span data-ttu-id="117d9-527">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="117d9-527">COLLATION</span></span>|<span data-ttu-id="117d9-528">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-528">Int16</span></span>|  
|<span data-ttu-id="117d9-529">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="117d9-529">CARDINALITY</span></span>|<span data-ttu-id="117d9-530">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="117d9-530">Decimal</span></span>|  
|<span data-ttu-id="117d9-531">STRONY</span><span class="sxs-lookup"><span data-stu-id="117d9-531">PAGES</span></span>|<span data-ttu-id="117d9-532">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-532">Int32</span></span>|  
|<span data-ttu-id="117d9-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="117d9-533">FILTER_CONDITION</span></span>|<span data-ttu-id="117d9-534">String</span><span class="sxs-lookup"><span data-stu-id="117d9-534">String</span></span>|  
|<span data-ttu-id="117d9-535">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="117d9-535">INTEGRATED</span></span>|<span data-ttu-id="117d9-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="117d9-537">Dostawca programu Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="117d9-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="117d9-538">Sterownik firmy Microsoft Jet OLE DB obsługuje następujące kolekcje określonego schematu, oprócz typowych kolekcje schematów:</span><span class="sxs-lookup"><span data-stu-id="117d9-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="117d9-539">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-539">Tables</span></span>  
  
-   <span data-ttu-id="117d9-540">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-540">Columns</span></span>  
  
-   <span data-ttu-id="117d9-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-541">Procedures</span></span>  
  
-   <span data-ttu-id="117d9-542">Widoki</span><span class="sxs-lookup"><span data-stu-id="117d9-542">Views</span></span>  
  
-   <span data-ttu-id="117d9-543">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="117d9-544">Tabele</span><span class="sxs-lookup"><span data-stu-id="117d9-544">Tables</span></span>  
  
|<span data-ttu-id="117d9-545">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-545">ColumnName</span></span>|<span data-ttu-id="117d9-546">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-547">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-548">String</span><span class="sxs-lookup"><span data-stu-id="117d9-548">String</span></span>|  
|<span data-ttu-id="117d9-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-550">String</span><span class="sxs-lookup"><span data-stu-id="117d9-550">String</span></span>|  
|<span data-ttu-id="117d9-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-551">TABLE_NAME</span></span>|<span data-ttu-id="117d9-552">String</span><span class="sxs-lookup"><span data-stu-id="117d9-552">String</span></span>|  
|<span data-ttu-id="117d9-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-553">TABLE_TYPE</span></span>|<span data-ttu-id="117d9-554">String</span><span class="sxs-lookup"><span data-stu-id="117d9-554">String</span></span>|  
|<span data-ttu-id="117d9-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-555">TABLE_GUID</span></span>|<span data-ttu-id="117d9-556">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-556">Guid</span></span>|  
|<span data-ttu-id="117d9-557">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-557">DESCRIPTION</span></span>|<span data-ttu-id="117d9-558">String</span><span class="sxs-lookup"><span data-stu-id="117d9-558">String</span></span>|  
|<span data-ttu-id="117d9-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-559">TABLE_PROPID</span></span>|<span data-ttu-id="117d9-560">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-560">Int64</span></span>|  
|<span data-ttu-id="117d9-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-561">DATE_CREATED</span></span>|<span data-ttu-id="117d9-562">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-562">DateTime</span></span>|  
|<span data-ttu-id="117d9-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-563">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-564">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="117d9-565">Kolumny</span><span class="sxs-lookup"><span data-stu-id="117d9-565">Columns</span></span>  
  
|<span data-ttu-id="117d9-566">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-566">ColumnName</span></span>|<span data-ttu-id="117d9-567">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-568">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-569">String</span><span class="sxs-lookup"><span data-stu-id="117d9-569">String</span></span>|  
|<span data-ttu-id="117d9-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-571">String</span><span class="sxs-lookup"><span data-stu-id="117d9-571">String</span></span>|  
|<span data-ttu-id="117d9-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-572">TABLE_NAME</span></span>|<span data-ttu-id="117d9-573">String</span><span class="sxs-lookup"><span data-stu-id="117d9-573">String</span></span>|  
|<span data-ttu-id="117d9-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-574">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-575">String</span><span class="sxs-lookup"><span data-stu-id="117d9-575">String</span></span>|  
|<span data-ttu-id="117d9-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-576">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-577">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-577">Guid</span></span>|  
|<span data-ttu-id="117d9-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-578">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-579">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-579">Int64</span></span>|  
|<span data-ttu-id="117d9-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-581">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-581">Int64</span></span>|  
|<span data-ttu-id="117d9-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="117d9-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-583">Boolean</span></span>|  
|<span data-ttu-id="117d9-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="117d9-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="117d9-585">String</span><span class="sxs-lookup"><span data-stu-id="117d9-585">String</span></span>|  
|<span data-ttu-id="117d9-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="117d9-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="117d9-587">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-587">Int64</span></span>|  
|<span data-ttu-id="117d9-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-588">IS_NULLABLE</span></span>|<span data-ttu-id="117d9-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-589">Boolean</span></span>|  
|<span data-ttu-id="117d9-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-590">DATA_TYPE</span></span>|<span data-ttu-id="117d9-591">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-591">Int32</span></span>|  
|<span data-ttu-id="117d9-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-592">TYPE_GUID</span></span>|<span data-ttu-id="117d9-593">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-593">Guid</span></span>|  
|<span data-ttu-id="117d9-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="117d9-595">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-595">Int64</span></span>|  
|<span data-ttu-id="117d9-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="117d9-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="117d9-597">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-597">Int64</span></span>|  
|<span data-ttu-id="117d9-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="117d9-599">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-599">Int32</span></span>|  
|<span data-ttu-id="117d9-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="117d9-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="117d9-601">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-601">Int16</span></span>|  
|<span data-ttu-id="117d9-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="117d9-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="117d9-603">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-603">Int64</span></span>|  
|<span data-ttu-id="117d9-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="117d9-605">String</span><span class="sxs-lookup"><span data-stu-id="117d9-605">String</span></span>|  
|<span data-ttu-id="117d9-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="117d9-607">String</span><span class="sxs-lookup"><span data-stu-id="117d9-607">String</span></span>|  
|<span data-ttu-id="117d9-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="117d9-609">String</span><span class="sxs-lookup"><span data-stu-id="117d9-609">String</span></span>|  
|<span data-ttu-id="117d9-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="117d9-611">String</span><span class="sxs-lookup"><span data-stu-id="117d9-611">String</span></span>|  
|<span data-ttu-id="117d9-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="117d9-613">String</span><span class="sxs-lookup"><span data-stu-id="117d9-613">String</span></span>|  
|<span data-ttu-id="117d9-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-614">COLLATION_NAME</span></span>|<span data-ttu-id="117d9-615">String</span><span class="sxs-lookup"><span data-stu-id="117d9-615">String</span></span>|  
|<span data-ttu-id="117d9-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="117d9-617">String</span><span class="sxs-lookup"><span data-stu-id="117d9-617">String</span></span>|  
|<span data-ttu-id="117d9-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="117d9-619">String</span><span class="sxs-lookup"><span data-stu-id="117d9-619">String</span></span>|  
|<span data-ttu-id="117d9-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-620">DOMAIN_NAME</span></span>|<span data-ttu-id="117d9-621">String</span><span class="sxs-lookup"><span data-stu-id="117d9-621">String</span></span>|  
|<span data-ttu-id="117d9-622">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-622">DESCRIPTION</span></span>|<span data-ttu-id="117d9-623">String</span><span class="sxs-lookup"><span data-stu-id="117d9-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="117d9-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="117d9-624">Procedures</span></span>  
  
|<span data-ttu-id="117d9-625">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-625">ColumnName</span></span>|<span data-ttu-id="117d9-626">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="117d9-628">String</span><span class="sxs-lookup"><span data-stu-id="117d9-628">String</span></span>|  
|<span data-ttu-id="117d9-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="117d9-630">String</span><span class="sxs-lookup"><span data-stu-id="117d9-630">String</span></span>|  
|<span data-ttu-id="117d9-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="117d9-632">String</span><span class="sxs-lookup"><span data-stu-id="117d9-632">String</span></span>|  
|<span data-ttu-id="117d9-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="117d9-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="117d9-634">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-634">Int16</span></span>|  
|<span data-ttu-id="117d9-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="117d9-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="117d9-636">String</span><span class="sxs-lookup"><span data-stu-id="117d9-636">String</span></span>|  
|<span data-ttu-id="117d9-637">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-637">DESCRIPTION</span></span>|<span data-ttu-id="117d9-638">String</span><span class="sxs-lookup"><span data-stu-id="117d9-638">String</span></span>|  
|<span data-ttu-id="117d9-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-639">DATE_CREATED</span></span>|<span data-ttu-id="117d9-640">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-640">DateTime</span></span>|  
|<span data-ttu-id="117d9-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-641">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-642">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="117d9-643">Widoki</span><span class="sxs-lookup"><span data-stu-id="117d9-643">Views</span></span>  
  
|<span data-ttu-id="117d9-644">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-644">ColumnName</span></span>|<span data-ttu-id="117d9-645">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-646">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-647">String</span><span class="sxs-lookup"><span data-stu-id="117d9-647">String</span></span>|  
|<span data-ttu-id="117d9-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-649">String</span><span class="sxs-lookup"><span data-stu-id="117d9-649">String</span></span>|  
|<span data-ttu-id="117d9-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-650">TABLE_NAME</span></span>|<span data-ttu-id="117d9-651">String</span><span class="sxs-lookup"><span data-stu-id="117d9-651">String</span></span>|  
|<span data-ttu-id="117d9-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="117d9-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="117d9-653">String</span><span class="sxs-lookup"><span data-stu-id="117d9-653">String</span></span>|  
|<span data-ttu-id="117d9-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="117d9-654">CHECK_OPTION</span></span>|<span data-ttu-id="117d9-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-655">Boolean</span></span>|  
|<span data-ttu-id="117d9-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="117d9-656">IS_UPDATABLE</span></span>|<span data-ttu-id="117d9-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-657">Boolean</span></span>|  
|<span data-ttu-id="117d9-658">OPIS ELEMENTU</span><span class="sxs-lookup"><span data-stu-id="117d9-658">DESCRIPTION</span></span>|<span data-ttu-id="117d9-659">String</span><span class="sxs-lookup"><span data-stu-id="117d9-659">String</span></span>|  
|<span data-ttu-id="117d9-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="117d9-660">DATE_CREATED</span></span>|<span data-ttu-id="117d9-661">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-661">DateTime</span></span>|  
|<span data-ttu-id="117d9-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="117d9-662">DATE_MODIFIED</span></span>|<span data-ttu-id="117d9-663">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="117d9-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="117d9-664">Indeksy</span><span class="sxs-lookup"><span data-stu-id="117d9-664">Indexes</span></span>  
  
|<span data-ttu-id="117d9-665">Element columnName</span><span class="sxs-lookup"><span data-stu-id="117d9-665">ColumnName</span></span>|<span data-ttu-id="117d9-666">Typ danych</span><span class="sxs-lookup"><span data-stu-id="117d9-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="117d9-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-667">TABLE_CATALOG</span></span>|<span data-ttu-id="117d9-668">String</span><span class="sxs-lookup"><span data-stu-id="117d9-668">String</span></span>|  
|<span data-ttu-id="117d9-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="117d9-670">String</span><span class="sxs-lookup"><span data-stu-id="117d9-670">String</span></span>|  
|<span data-ttu-id="117d9-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-671">TABLE_NAME</span></span>|<span data-ttu-id="117d9-672">String</span><span class="sxs-lookup"><span data-stu-id="117d9-672">String</span></span>|  
|<span data-ttu-id="117d9-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="117d9-673">INDEX_CATALOG</span></span>|<span data-ttu-id="117d9-674">String</span><span class="sxs-lookup"><span data-stu-id="117d9-674">String</span></span>|  
|<span data-ttu-id="117d9-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="117d9-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="117d9-676">String</span><span class="sxs-lookup"><span data-stu-id="117d9-676">String</span></span>|  
|<span data-ttu-id="117d9-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-677">INDEX_NAME</span></span>|<span data-ttu-id="117d9-678">String</span><span class="sxs-lookup"><span data-stu-id="117d9-678">String</span></span>|  
|<span data-ttu-id="117d9-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="117d9-679">PRIMARY_KEY</span></span>|<span data-ttu-id="117d9-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-680">Boolean</span></span>|  
|<span data-ttu-id="117d9-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="117d9-681">UNIQUE</span></span>|<span data-ttu-id="117d9-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-682">Boolean</span></span>|  
|<span data-ttu-id="117d9-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="117d9-683">CLUSTERED</span></span>|<span data-ttu-id="117d9-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-684">Boolean</span></span>|  
|<span data-ttu-id="117d9-685">TYP</span><span class="sxs-lookup"><span data-stu-id="117d9-685">TYPE</span></span>|<span data-ttu-id="117d9-686">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-686">Int32</span></span>|  
|<span data-ttu-id="117d9-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="117d9-687">FILL_FACTOR</span></span>|<span data-ttu-id="117d9-688">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-688">Int32</span></span>|  
|<span data-ttu-id="117d9-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="117d9-689">INITIAL_SIZE</span></span>|<span data-ttu-id="117d9-690">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-690">Int32</span></span>|  
|<span data-ttu-id="117d9-691">NULL — Wartości</span><span class="sxs-lookup"><span data-stu-id="117d9-691">NULLS</span></span>|<span data-ttu-id="117d9-692">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-692">Int32</span></span>|  
|<span data-ttu-id="117d9-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="117d9-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="117d9-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-694">Boolean</span></span>|  
|<span data-ttu-id="117d9-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="117d9-695">AUTO_UPDATE</span></span>|<span data-ttu-id="117d9-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-696">Boolean</span></span>|  
|<span data-ttu-id="117d9-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="117d9-697">NULL_COLLATION</span></span>|<span data-ttu-id="117d9-698">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-698">Int32</span></span>|  
|<span data-ttu-id="117d9-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="117d9-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="117d9-700">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-700">Int64</span></span>|  
|<span data-ttu-id="117d9-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="117d9-701">COLUMN_NAME</span></span>|<span data-ttu-id="117d9-702">String</span><span class="sxs-lookup"><span data-stu-id="117d9-702">String</span></span>|  
|<span data-ttu-id="117d9-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-703">COLUMN_GUID</span></span>|<span data-ttu-id="117d9-704">Identyfikator GUID</span><span class="sxs-lookup"><span data-stu-id="117d9-704">Guid</span></span>|  
|<span data-ttu-id="117d9-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="117d9-705">COLUMN_PROPID</span></span>|<span data-ttu-id="117d9-706">Int64</span><span class="sxs-lookup"><span data-stu-id="117d9-706">Int64</span></span>|  
|<span data-ttu-id="117d9-707">SORTOWANIE</span><span class="sxs-lookup"><span data-stu-id="117d9-707">COLLATION</span></span>|<span data-ttu-id="117d9-708">Int16</span><span class="sxs-lookup"><span data-stu-id="117d9-708">Int16</span></span>|  
|<span data-ttu-id="117d9-709">KARDYNALNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="117d9-709">CARDINALITY</span></span>|<span data-ttu-id="117d9-710">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="117d9-710">Decimal</span></span>|  
|<span data-ttu-id="117d9-711">STRONY</span><span class="sxs-lookup"><span data-stu-id="117d9-711">PAGES</span></span>|<span data-ttu-id="117d9-712">Int32</span><span class="sxs-lookup"><span data-stu-id="117d9-712">Int32</span></span>|  
|<span data-ttu-id="117d9-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="117d9-713">FILTER_CONDITION</span></span>|<span data-ttu-id="117d9-714">String</span><span class="sxs-lookup"><span data-stu-id="117d9-714">String</span></span>|  
|<span data-ttu-id="117d9-715">ZINTEGROWANE</span><span class="sxs-lookup"><span data-stu-id="117d9-715">INTEGRATED</span></span>|<span data-ttu-id="117d9-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="117d9-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="117d9-717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="117d9-717">See Also</span></span>  
 [<span data-ttu-id="117d9-718">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="117d9-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
