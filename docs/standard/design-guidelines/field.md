---
title: Pole projektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571120"
---
# <a name="field-design"></a><span data-ttu-id="9fc19-102">Pole projektu</span><span class="sxs-lookup"><span data-stu-id="9fc19-102">Field Design</span></span>
<span data-ttu-id="9fc19-103">Zasada hermetyzacji jest jednym z najważniejsze koncepcje zorientowane obiektowo projektu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="9fc19-104">Ta zasada mówi, że dane przechowywane wewnątrz obiektu powinien być dostępny tylko dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="9fc19-105">Jest wygodny sposób, aby zinterpretować zasady oznacza, że typ należy tak zaprojektować, dzięki czemu można wprowadzać zmiany do pól typu (zmiany nazwy lub typu) bez przerywania kodu innego niż dla elementów członkowskich tego typu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="9fc19-106">Niniejsza interpretacja natychmiast oznacza, że wszystkie pola muszą być prywatne.</span><span class="sxs-lookup"><span data-stu-id="9fc19-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="9fc19-107">Wyłączamy stałej i statycznego pola tylko do odczytu z tego ograniczenia strict, ponieważ takie pola prawie zgodnie z definicją nigdy nie wymaga zmiany.</span><span class="sxs-lookup"><span data-stu-id="9fc19-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="9fc19-108">**X nie** Podaj pól wystąpień, które są publiczne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="9fc19-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="9fc19-109">Należy podać właściwości do uzyskiwania dostępu do pola zamiast nadawania publiczne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="9fc19-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="9fc19-110">**CZY ✓** Użyj stałych pól na stałe, które nigdy nie zmieni.</span><span class="sxs-lookup"><span data-stu-id="9fc19-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="9fc19-111">Kompilator pali wartości pól const bezpośrednio do wywoływania z kodu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="9fc19-112">W związku z tym wartości stałych nigdy nie można zmienić bez ryzyka fundamentalne zgodności.</span><span class="sxs-lookup"><span data-stu-id="9fc19-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="9fc19-113">**CZY ✓** Użyj publiczne statyczne `readonly` pól dla wstępnie zdefiniowanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="9fc19-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="9fc19-114">W przypadku wystąpienia wstępnie zdefiniowanego typu zadeklarować je jako publiczną pola statycznego tylko do odczytu tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="9fc19-115">**X nie** przypisać wystąpień typów modyfikowalną do `readonly` pola.</span><span class="sxs-lookup"><span data-stu-id="9fc19-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="9fc19-116">Modyfikowalne typ jest typem z wystąpieniami, które można zmodyfikować po utrzymującego.</span><span class="sxs-lookup"><span data-stu-id="9fc19-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="9fc19-117">Na przykład tablic, większość kolekcji i strumienie są modyfikowalne typów, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, i <xref:System.String?displayProperty=nameWithType> są niezmienne wszystkie.</span><span class="sxs-lookup"><span data-stu-id="9fc19-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="9fc19-118">Wystąpienie przechowywana w polu od zastępowanego uniemożliwia modyfikatora tylko do odczytu w polu typu odwołania, ale nie zapobiega danych wystąpienia w polu przed modyfikacją przez wywołanie członków zmiana wystąpienia programu.</span><span class="sxs-lookup"><span data-stu-id="9fc19-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="9fc19-119">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="9fc19-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9fc19-120">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="9fc19-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc19-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fc19-121">See Also</span></span>  
 [<span data-ttu-id="9fc19-122">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9fc19-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="9fc19-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="9fc19-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
