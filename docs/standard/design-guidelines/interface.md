---
title: Projekt interfejsu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573042"
---
# <a name="interface-design"></a><span data-ttu-id="da419-102">Projekt interfejsu</span><span class="sxs-lookup"><span data-stu-id="da419-102">Interface Design</span></span>
<span data-ttu-id="da419-103">Mimo że większość interfejsów API najlepiej są modelowane przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub tylko opcja.</span><span class="sxs-lookup"><span data-stu-id="da419-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="da419-104">Środowisko CLR nie obsługuje dziedziczenie wielokrotne (tj. klasy CLR nie może dziedziczyć z więcej niż jedną klasę podstawową), ale możliwe typy zaimplementować jeden lub więcej interfejsów oprócz dziedziczenia z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="da419-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="da419-105">W związku z tym interfejsy są często używane do uzyskania wpływu dziedziczenie wielokrotne.</span><span class="sxs-lookup"><span data-stu-id="da419-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="da419-106">Na przykład <xref:System.IDisposable> jest interfejs, umożliwiający typy do obsługi disposability niezależnie od innych hierarchii dziedziczenia, w którym chcesz brać udział.</span><span class="sxs-lookup"><span data-stu-id="da419-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="da419-107">Sytuacja, w których definiowanie interfejsu jest jest przy tworzeniu wspólnego interfejsu, który może być obsługiwany przez kilka typów, w tym niektórych typów wartości.</span><span class="sxs-lookup"><span data-stu-id="da419-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="da419-108">Typy wartości nie może dziedziczyć z typów innych niż <xref:System.ValueType>, ale miały zaimplementowane interfejsy, za pomocą interfejsu jest jedyną opcją w celu zapewnienia wspólnego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="da419-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="da419-109">**CZY ✓** interfejs umożliwia określenie, czy należy niektórych typowych interfejsu API, obsługiwane przez zestaw typów, który zawiera typy wartości.</span><span class="sxs-lookup"><span data-stu-id="da419-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="da419-110">**ROZWAŻ ✓** Definiowanie interfejsu, jeśli zachodzi konieczność obsługi jej funkcji dla typów dziedziczących z innego typu.</span><span class="sxs-lookup"><span data-stu-id="da419-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="da419-111">**X należy UNIKAĆ** za pomocą znacznika interfejsów (interfejsy bez członków).</span><span class="sxs-lookup"><span data-stu-id="da419-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="da419-112">Jeśli potrzebujesz Oznacz klasę jako mający określonej właściwości (znacznik), ogólnie rzecz biorąc, użyj atrybutu niestandardowego zamiast interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="da419-113">**CZY ✓** Podaj co najmniej jeden typ, który jest implementacją interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="da419-114">Wykonywanie dzięki temu można sprawdzić poprawności projektu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="da419-115">Na przykład <xref:System.Collections.Generic.List%601> jest implementacją <xref:System.Collections.Generic.IList%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="da419-116">**CZY ✓** Podaj co najmniej jeden interfejs API, który wykorzystuje każdego interfejsu należy zdefiniować (metody interfejsu jako parametr lub właściwość typu interfejsu).</span><span class="sxs-lookup"><span data-stu-id="da419-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="da419-117">Wykonywanie dzięki temu można sprawdzić poprawności projektu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="da419-118">Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> zużywa <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="da419-119">**X nie** dodawać członków do interfejsu, która została wcześniej dostarczona.</span><span class="sxs-lookup"><span data-stu-id="da419-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="da419-120">W ten sposób spowoduje przerwanie implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da419-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="da419-121">Aby uniknąć problemów z kontroli wersji, należy utworzyć nowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="da419-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="da419-122">Z wyjątkiem sytuacji opisanych w poniższych wskazówek ogólnie rzecz biorąc, wybierz klasy, a nie interfejsy projektowanie biblioteki do ponownego użycia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="da419-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="da419-123">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="da419-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="da419-124">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="da419-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da419-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da419-125">See Also</span></span>  
 [<span data-ttu-id="da419-126">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="da419-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="da419-127">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="da419-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
