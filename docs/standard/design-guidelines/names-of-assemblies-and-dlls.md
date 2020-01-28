---
title: Nazwy zestawów i bibliotek DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: f3c5997f777c937e9726b271afa0ae6d7a19b37d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744174"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="62109-102">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="62109-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="62109-103">Zestaw jest jednostką wdrożenia i tożsamością dla programów kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="62109-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="62109-104">Chociaż zestawy mogą obejmować jeden lub więcej plików, zazwyczaj zestaw mapuje jeden do jednego z biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="62109-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="62109-105">W związku z tym, w tej sekcji opisano tylko konwencje nazewnictwa bibliotek DLL, które następnie można mapować na konwencje nazewnictwa zestawów.</span><span class="sxs-lookup"><span data-stu-id="62109-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>

 <span data-ttu-id="62109-106">✔️ Wybierz nazwy bibliotek DLL zestawu, które sugerują duże fragmenty funkcjonalności, takich jak system. Data.</span><span class="sxs-lookup"><span data-stu-id="62109-106">✔️ DO choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>

 <span data-ttu-id="62109-107">Nazwy zestawów i bibliotek DLL nie muszą odpowiadać nazwom przestrzeni nazw, ale podczas określania nazw zestawów można przestrzegać nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="62109-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="62109-108">Dobrą regułą dla kciuka jest nazwa biblioteki DLL na podstawie wspólnego prefiksu przestrzeni nazw zawartych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="62109-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="62109-109">Na przykład zestaw zawierający dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być nazywany `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="62109-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>

 <span data-ttu-id="62109-110">✔️ ROZWAŻYĆ nazewnictwa bibliotek DLL zgodnie z poniższym wzorcem:</span><span class="sxs-lookup"><span data-stu-id="62109-110">✔️ CONSIDER naming DLLs according to the following pattern:</span></span>

 `<Company>.<Component>.dll`

 <span data-ttu-id="62109-111">gdzie `<Component>` zawiera jedną lub więcej klauzul rozdzielonych kropkami.</span><span class="sxs-lookup"><span data-stu-id="62109-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="62109-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="62109-112">For example:</span></span>

 <span data-ttu-id="62109-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="62109-113">`Litware.Controls.dll`.</span></span>

 <span data-ttu-id="62109-114">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="62109-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="62109-115">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="62109-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="62109-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62109-116">See also</span></span>

- [<span data-ttu-id="62109-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="62109-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="62109-118">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="62109-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
