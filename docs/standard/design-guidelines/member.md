---
title: Element członkowski — zalecenia dotyczące projektowania
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1598ac63af38f1ca3e11104bc8e1cd6323d35ed
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190179"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="45d2b-102">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="45d2b-102">Member Design Guidelines</span></span>
<span data-ttu-id="45d2b-103">Metody, właściwości, zdarzenia, konstruktory i pola są nazywane zbiorczo elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="45d2b-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="45d2b-104">Elementy członkowskie są ostatecznie oznacza, że za pomocą którego funkcja framework jest widoczna dla użytkowników końcowych RAM.</span><span class="sxs-lookup"><span data-stu-id="45d2b-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="45d2b-105">Członkowie mogą być wirtualne lub niewirtualne, konkretny ani abstrakcyjne, statyczne lub wystąpienie i może mieć kilka różnych zakresów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="45d2b-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="45d2b-106">Takiej odmiany zapewnia niezwykłą wyrazistość, ale w tym samym czasie wymaga obsługi ze strony Projektant framework.</span><span class="sxs-lookup"><span data-stu-id="45d2b-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="45d2b-107">W tym rozdziale oferuje podstawowe wytyczne, które należy stosować podczas projektowania składowe dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="45d2b-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45d2b-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45d2b-108">In This Section</span></span>  
 [<span data-ttu-id="45d2b-109">Przeciążanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="45d2b-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="45d2b-110">Projekt właściwości</span><span class="sxs-lookup"><span data-stu-id="45d2b-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="45d2b-111">Projekt konstruktora</span><span class="sxs-lookup"><span data-stu-id="45d2b-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="45d2b-112">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="45d2b-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="45d2b-113">Projekt pola</span><span class="sxs-lookup"><span data-stu-id="45d2b-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="45d2b-114">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="45d2b-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="45d2b-115">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="45d2b-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="45d2b-116">Projekt parametrów</span><span class="sxs-lookup"><span data-stu-id="45d2b-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="45d2b-117">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="45d2b-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="45d2b-118">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="45d2b-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d2b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45d2b-119">See also</span></span>

- [<span data-ttu-id="45d2b-120">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="45d2b-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
