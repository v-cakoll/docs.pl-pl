---
title: Składowa — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: c323e7edd752a1f003bd3f5d81689aca0eaefd20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288995"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="e5c40-102">Składowa — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="e5c40-102">Member Design Guidelines</span></span>
<span data-ttu-id="e5c40-103">Metody, właściwości, zdarzenia, konstruktory i pola są zbiorczo nazywane elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="e5c40-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="e5c40-104">Członkowie są ostatecznie sposobem, przez który funkcje platformy są udostępniane użytkownikom końcowym struktury.</span><span class="sxs-lookup"><span data-stu-id="e5c40-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="e5c40-105">Elementy członkowskie mogą być wirtualne lub niewirtualne, konkretne lub abstrakcyjne, statyczne lub wystąpienia oraz mogą mieć kilka różnych zakresów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="e5c40-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="e5c40-106">Cała ta odmiana zawiera niesamowitą wyrazistości, ale w tym samym czasie wymaga zaopieki nad częścią projektanta struktury.</span><span class="sxs-lookup"><span data-stu-id="e5c40-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="e5c40-107">Ten rozdział zawiera podstawowe wytyczne, które należy stosować podczas projektowania członków dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="e5c40-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5c40-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e5c40-108">In This Section</span></span>  
 [<span data-ttu-id="e5c40-109">Przeciążenie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="e5c40-109">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="e5c40-110">Projekt właściwości</span><span class="sxs-lookup"><span data-stu-id="e5c40-110">Property Design</span></span>](property.md)  
 [<span data-ttu-id="e5c40-111">Projekt konstruktora</span><span class="sxs-lookup"><span data-stu-id="e5c40-111">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="e5c40-112">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e5c40-112">Event Design</span></span>](event.md)  
 [<span data-ttu-id="e5c40-113">Projekt pola</span><span class="sxs-lookup"><span data-stu-id="e5c40-113">Field Design</span></span>](field.md)  
 [<span data-ttu-id="e5c40-114">Metody rozszerzania</span><span class="sxs-lookup"><span data-stu-id="e5c40-114">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="e5c40-115">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="e5c40-115">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="e5c40-116">Projekt parametru</span><span class="sxs-lookup"><span data-stu-id="e5c40-116">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="e5c40-117">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="e5c40-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e5c40-118">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="e5c40-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c40-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5c40-119">See also</span></span>

- [<span data-ttu-id="e5c40-120">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="e5c40-120">Framework Design Guidelines</span></span>](index.md)
