---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621250"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="70f5d-101">Trwałość SQL przepływu pracy dodaje klastry kluczy podstawowych i nie zezwala na wartości null w niektórych kolumnach</span><span class="sxs-lookup"><span data-stu-id="70f5d-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="70f5d-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="70f5d-102">Details</span></span>

<span data-ttu-id="70f5d-103">Począwszy od .NET Framework 4,7, tabele utworzone dla magazynu wystąpienia przepływu pracy SQL (SWIS) przez skrypt SqlWorkflowInstanceStoreSchema. SQL używają klastrowanych kluczy podstawowych.</span><span class="sxs-lookup"><span data-stu-id="70f5d-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="70f5d-104">Z tego powodu tożsamości nie obsługują <code>null</code> wartości.</span><span class="sxs-lookup"><span data-stu-id="70f5d-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="70f5d-105">Ta zmiana nie ma wpływu na operację SWIS.</span><span class="sxs-lookup"><span data-stu-id="70f5d-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="70f5d-106">Wprowadzono aktualizacje obsługujące SQL Server replikację transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="70f5d-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70f5d-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="70f5d-107">Suggestion</span></span>

<span data-ttu-id="70f5d-108">Aby można było obsłużyć tę zmianę, należy zastosować plik SQL SqlWorkflowInstanceStoreSchemaUpgrade. SQL do istniejących instalacji.</span><span class="sxs-lookup"><span data-stu-id="70f5d-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="70f5d-109">Nowe instalacje baz danych zostaną automatycznie zmienione.</span><span class="sxs-lookup"><span data-stu-id="70f5d-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="70f5d-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="70f5d-110">Name</span></span>    | <span data-ttu-id="70f5d-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="70f5d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70f5d-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="70f5d-112">Scope</span></span>   |<span data-ttu-id="70f5d-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="70f5d-113">Edge</span></span>|
|<span data-ttu-id="70f5d-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="70f5d-114">Version</span></span>|<span data-ttu-id="70f5d-115">4,7</span><span class="sxs-lookup"><span data-stu-id="70f5d-115">4.7</span></span>|
|<span data-ttu-id="70f5d-116">Typ</span><span class="sxs-lookup"><span data-stu-id="70f5d-116">Type</span></span>|<span data-ttu-id="70f5d-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="70f5d-117">Runtime</span></span>|
