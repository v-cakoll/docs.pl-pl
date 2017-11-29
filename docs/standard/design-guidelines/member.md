---
title: "Wytyczne dotyczące projektowania elementu członkowskiego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5df4ad5f6c947d8b3bf62c3bf7eb8426419e5f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="member-design-guidelines"></a><span data-ttu-id="62ff7-102">Wytyczne dotyczące projektowania elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="62ff7-102">Member Design Guidelines</span></span>
<span data-ttu-id="62ff7-103">Metody, właściwości, zdarzenia, konstruktorów i pól zbiorowo są określane jako elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="62ff7-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="62ff7-104">Elementy członkowskie są ostatecznie oznacza za pomocą którego funkcji framework jest narażony na użytkowników końcowych RAM.</span><span class="sxs-lookup"><span data-stu-id="62ff7-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="62ff7-105">Elementy Członkowskie mogą być statyczne wirtualnych lub niewirtualne, konkretnych lub abstrakcyjny, lub wystąpienia, a może mieć kilka różnych zakresów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="62ff7-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="62ff7-106">Takiej odmiany zapewnia wyrazistość wyjątkowo, ale w tym samym czasie wymaga opieki ze strony projektanta framework.</span><span class="sxs-lookup"><span data-stu-id="62ff7-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="62ff7-107">Ten rozdział zawiera podstawowe wskazówki, które należy wykonać podczas projektowania elementów członkowskich dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="62ff7-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62ff7-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="62ff7-108">In This Section</span></span>  
 [<span data-ttu-id="62ff7-109">Przeciążenie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="62ff7-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="62ff7-110">Właściwości projektu</span><span class="sxs-lookup"><span data-stu-id="62ff7-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="62ff7-111">Projekt — Konstruktor</span><span class="sxs-lookup"><span data-stu-id="62ff7-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="62ff7-112">Projekt zdarzeń</span><span class="sxs-lookup"><span data-stu-id="62ff7-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="62ff7-113">Pole projektu</span><span class="sxs-lookup"><span data-stu-id="62ff7-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="62ff7-114">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="62ff7-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="62ff7-115">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="62ff7-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="62ff7-116">Parametr projektu</span><span class="sxs-lookup"><span data-stu-id="62ff7-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="62ff7-117">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="62ff7-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="62ff7-118">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="62ff7-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ff7-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62ff7-119">See Also</span></span>  
 [<span data-ttu-id="62ff7-120">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="62ff7-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
