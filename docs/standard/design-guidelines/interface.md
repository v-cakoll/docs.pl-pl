---
title: Projekt interfejsu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026370"
---
# <a name="interface-design"></a><span data-ttu-id="77b19-102">Projekt interfejsu</span><span class="sxs-lookup"><span data-stu-id="77b19-102">Interface Design</span></span>
<span data-ttu-id="77b19-103">Mimo że większość interfejsów API najlepiej są modelowane przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub są jedynym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="77b19-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="77b19-104">Środowisko CLR nie obsługuje dziedziczenie wielokrotne (czyli klas CLR nie może dziedziczyć z więcej niż jednej klasy bazowej), ale zezwala na typy zaimplementować jeden lub więcej interfejsów oprócz dziedziczy z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="77b19-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="77b19-105">W związku z tym interfejsy są często używane, aby osiągnąć ten efekt wielokrotnego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="77b19-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="77b19-106">Na przykład <xref:System.IDisposable> jest interfejsem, który zezwala na typy do obsługi disposability niezależnie od innych hierarchii dziedziczenia, w którym chcesz uczestniczyć.</span><span class="sxs-lookup"><span data-stu-id="77b19-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="77b19-107">Sytuacja, w określeniu, które jest odpowiednie interfejs znajduje się w tworzenie wspólny interfejs, który może być obsługiwany przez kilka typów, w tym niektóre typy wartości.</span><span class="sxs-lookup"><span data-stu-id="77b19-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="77b19-108">Typy wartości nie może dziedziczyć z typu innego niż <xref:System.ValueType>, ale mogące implementować interfejsy, za pomocą interfejsu jest jedyną opcją, aby zapewnić wspólny typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="77b19-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="77b19-109">**✓ DO** interfejs umożliwia określenie, czy należy niektórych typowych interfejsu API, obsługiwane przez zestaw typów, który zawiera typy wartości.</span><span class="sxs-lookup"><span data-stu-id="77b19-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="77b19-110">**✓ CONSIDER** Definiowanie interfejsu, jeśli zachodzi konieczność obsługi jej funkcji dla typów dziedziczących z innego typu.</span><span class="sxs-lookup"><span data-stu-id="77b19-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="77b19-111">**X AVOID** za pomocą znacznika interfejsów (interfejsy bez członków).</span><span class="sxs-lookup"><span data-stu-id="77b19-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="77b19-112">Jeśli potrzebujesz oznaczyć klasę jako posiadające szczególne cechy (znacznik), ogólnie rzecz biorąc, użyj atrybutu niestandardowego, a nie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="77b19-113">**✓ DO** Podaj co najmniej jeden typ, który jest implementacją interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="77b19-114">Wykonując pozwala sprawdzić projekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="77b19-115">Na przykład <xref:System.Collections.Generic.List%601> jest implementacją <xref:System.Collections.Generic.IList%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="77b19-116">**✓ DO** Podaj co najmniej jeden interfejs API, który wykorzystuje każdego interfejsu należy zdefiniować (metody interfejsu jako parametr lub właściwość typu interfejsu).</span><span class="sxs-lookup"><span data-stu-id="77b19-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="77b19-117">Wykonując pozwala sprawdzić projekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="77b19-118">Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> zużywa <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="77b19-119">**X DO NOT** dodawać członków do interfejsu, która została wcześniej dostarczona.</span><span class="sxs-lookup"><span data-stu-id="77b19-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="77b19-120">To spowoduje przerwanie implementacje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="77b19-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="77b19-121">Aby zapobiec problemom z wersjami, należy utworzyć nowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="77b19-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="77b19-122">Z wyjątkiem sytuacji określonych w niniejszych wytycznych ogólnie rzecz biorąc, wybierz klasy, a nie interfejsy projektowanie biblioteki do ponownego wykorzystania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="77b19-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="77b19-123">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="77b19-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="77b19-124">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="77b19-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b19-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77b19-125">See also</span></span>

- [<span data-ttu-id="77b19-126">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="77b19-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="77b19-127">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="77b19-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
