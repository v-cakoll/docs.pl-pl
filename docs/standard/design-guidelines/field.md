---
title: Projekt pola
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 34c5a163e545b78c188f37b2819962b4c7c56f80
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144354"
---
# <a name="field-design"></a><span data-ttu-id="b7e55-102">Projekt pola</span><span class="sxs-lookup"><span data-stu-id="b7e55-102">Field Design</span></span>
<span data-ttu-id="b7e55-103">Zasadą hermetyzacji jest jedną z najważniejszych koncepcje programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="b7e55-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="b7e55-104">Ta zasada mówi, dane przechowywane w ramach obiektu należy dostępny tylko dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b7e55-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="b7e55-105">Jest to przydatny sposób interpretowania zasady powiedzieć, że typem powinny zostać tak zaprojektowane, aby do pól typu (zmiany nazwy lub typu) zmian bez przerywania kodu innego niż dla elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="b7e55-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="b7e55-106">Interpretacja tego natychmiast oznacza, że wszystkie pola, muszą być w prywatnej.</span><span class="sxs-lookup"><span data-stu-id="b7e55-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="b7e55-107">Firma Microsoft Wyklucz stała i statycznego pola tylko do odczytu z to ścisłe ograniczenie, ponieważ takie pola prawie zgodnie z definicją, nigdy nie wymagana jest zmiana.</span><span class="sxs-lookup"><span data-stu-id="b7e55-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="b7e55-108">**X DO NOT** Podaj pól wystąpień, które są publiczne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="b7e55-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="b7e55-109">Należy podać właściwości do uzyskiwania dostępu do pola, a nie nadawania publiczne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="b7e55-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="b7e55-110">**✓ DO** Użyj stałych pól na stałe, które nigdy nie zmieni.</span><span class="sxs-lookup"><span data-stu-id="b7e55-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="b7e55-111">Kompilator spala wartości const pól bezpośrednio do wywoływania z kodu.</span><span class="sxs-lookup"><span data-stu-id="b7e55-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="b7e55-112">W związku z tym wartości stałych nigdy nie można zmienić bez przerywania zgodność ryzyka.</span><span class="sxs-lookup"><span data-stu-id="b7e55-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="b7e55-113">**✓ DO** Użyj publiczne statyczne `readonly` pól dla wstępnie zdefiniowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="b7e55-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="b7e55-114">W przypadku wstępnie zdefiniowanych wystąpień tego typu je zadeklarować jako tylko do odczytu statyczne pola publiczne samego typu.</span><span class="sxs-lookup"><span data-stu-id="b7e55-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="b7e55-115">**X DO NOT** przypisać wystąpień typów modyfikowalną do `readonly` pola.</span><span class="sxs-lookup"><span data-stu-id="b7e55-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="b7e55-116">Typ zmienny to typ z wystąpieniami, które mogą być modyfikowane po ich są tworzone.</span><span class="sxs-lookup"><span data-stu-id="b7e55-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="b7e55-117">Na przykład, tablice, większość kolekcji i strumienie są modyfikowalnych typów, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, i <xref:System.String?displayProperty=nameWithType> są wszystkie niezmienne.</span><span class="sxs-lookup"><span data-stu-id="b7e55-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="b7e55-118">Modyfikator tylko do odczytu w polu typu odwołania uniemożliwia wystąpienie przechowywane w polu od zastępowanego, ale nie uniemożliwia danych wystąpienia w polu przed modyfikacją, wywołując elementy zmiana wystąpienia programu.</span><span class="sxs-lookup"><span data-stu-id="b7e55-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="b7e55-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="b7e55-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b7e55-120">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="b7e55-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e55-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7e55-121">See also</span></span>

- [<span data-ttu-id="b7e55-122">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b7e55-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="b7e55-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b7e55-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
