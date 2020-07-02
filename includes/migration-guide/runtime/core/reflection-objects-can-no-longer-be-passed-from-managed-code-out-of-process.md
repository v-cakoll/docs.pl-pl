---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621334"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="8373a-101">Obiektów odbicia nie można już przekazywać z kodu zarządzanego do pozaprocesowych klientów DCOM.</span><span class="sxs-lookup"><span data-stu-id="8373a-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="8373a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8373a-102">Details</span></span>

<span data-ttu-id="8373a-103">Obiektów odbicia nie można już przekazywać z kodu zarządzanego do pozaprocesowych klientów DCOM.</span><span class="sxs-lookup"><span data-stu-id="8373a-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="8373a-104">Dotyczy to następujących typów:</span><span class="sxs-lookup"><span data-stu-id="8373a-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="8373a-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName>(i jego typy pochodne, w tym <xref:System.Reflection.FieldInfo?displayProperty=fullName> , <xref:System.Reflection.MethodInfo?displayProperty=fullName> , <xref:System.Type?displayProperty=fullName> i <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</span><span class="sxs-lookup"><span data-stu-id="8373a-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="8373a-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="8373a-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="8373a-107">Wywołania do <code>IMarshal</code> zwracanego obiektu <code>E_NOINTERFACE</code> .</span><span class="sxs-lookup"><span data-stu-id="8373a-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8373a-108">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8373a-108">Suggestion</span></span>

<span data-ttu-id="8373a-109">Aktualizuj kod kierujący do pracy z obiektami nieodbicia</span><span class="sxs-lookup"><span data-stu-id="8373a-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="8373a-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8373a-110">Name</span></span>    | <span data-ttu-id="8373a-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="8373a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8373a-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="8373a-112">Scope</span></span>   |<span data-ttu-id="8373a-113">Mały</span><span class="sxs-lookup"><span data-stu-id="8373a-113">Minor</span></span>|
|<span data-ttu-id="8373a-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="8373a-114">Version</span></span>|<span data-ttu-id="8373a-115">4.6</span><span class="sxs-lookup"><span data-stu-id="8373a-115">4.6</span></span>|
|<span data-ttu-id="8373a-116">Typ</span><span class="sxs-lookup"><span data-stu-id="8373a-116">Type</span></span>|<span data-ttu-id="8373a-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8373a-117">Runtime</span></span>|
