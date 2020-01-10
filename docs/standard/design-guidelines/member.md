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
ms.openlocfilehash: cf4f1d2fee73e3e65dc4d92ea97a62f4a7e4c4e5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709273"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="ac690-102">Składowa — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ac690-102">Member Design Guidelines</span></span>
<span data-ttu-id="ac690-103">Metody, właściwości, zdarzenia, konstruktory i pola są zbiorczo nazywane elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="ac690-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="ac690-104">Członkowie są ostatecznie sposobem, przez który funkcje platformy są udostępniane użytkownikom końcowym struktury.</span><span class="sxs-lookup"><span data-stu-id="ac690-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="ac690-105">Elementy członkowskie mogą być wirtualne lub niewirtualne, konkretne lub abstrakcyjne, statyczne lub wystąpienia oraz mogą mieć kilka różnych zakresów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="ac690-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="ac690-106">Cała ta odmiana zawiera niesamowitą wyrazistości, ale w tym samym czasie wymaga zaopieki nad częścią projektanta struktury.</span><span class="sxs-lookup"><span data-stu-id="ac690-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="ac690-107">Ten rozdział zawiera podstawowe wytyczne, które należy stosować podczas projektowania członków dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="ac690-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac690-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ac690-108">In This Section</span></span>  
 [<span data-ttu-id="ac690-109">Przeciążanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ac690-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="ac690-110">Projekt właściwości</span><span class="sxs-lookup"><span data-stu-id="ac690-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="ac690-111">Projekt konstruktora</span><span class="sxs-lookup"><span data-stu-id="ac690-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="ac690-112">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ac690-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="ac690-113">Projekt pola</span><span class="sxs-lookup"><span data-stu-id="ac690-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="ac690-114">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="ac690-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="ac690-115">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="ac690-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="ac690-116">Projekt parametrów</span><span class="sxs-lookup"><span data-stu-id="ac690-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="ac690-117">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ac690-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ac690-118">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="ac690-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac690-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac690-119">See also</span></span>

- [<span data-ttu-id="ac690-120">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ac690-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
