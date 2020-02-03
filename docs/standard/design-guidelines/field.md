---
title: Projekt pola
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: c00929ca499e39bd4e24d482c9413beb9cccddc1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741606"
---
# <a name="field-design"></a><span data-ttu-id="b3eac-102">Projekt pola</span><span class="sxs-lookup"><span data-stu-id="b3eac-102">Field Design</span></span>
<span data-ttu-id="b3eac-103">Zasada hermetyzacji jest jednym z najważniejszych koncepcji w projekcie zorientowanym na obiekty.</span><span class="sxs-lookup"><span data-stu-id="b3eac-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="b3eac-104">Ta zasada Określa, że dane przechowywane wewnątrz obiektu powinny być dostępne tylko dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3eac-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="b3eac-105">Przydatnym sposobem interpretacji zasady jest to, że typ powinien zostać zaprojektowany tak, aby zmiany w polach tego typu (zmiany nazwy lub typu) mogły zostać wykonane bez przerywania kodu innego niż dla elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="b3eac-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="b3eac-106">Ta interpretacja natychmiast oznacza, że wszystkie pola muszą być prywatne.</span><span class="sxs-lookup"><span data-stu-id="b3eac-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="b3eac-107">Wykluczamy stałe i statyczne pola tylko do odczytu z tego rygorystycznego ograniczenia, ponieważ takie pola, prawie według definicji, nigdy nie są wymagane do zmiany.</span><span class="sxs-lookup"><span data-stu-id="b3eac-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="b3eac-108">❌ nie zapewniają publicznych lub chronionych pól wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b3eac-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="b3eac-109">Należy podać właściwości dostępu do pól zamiast udostępniać je publicznie lub chronionym.</span><span class="sxs-lookup"><span data-stu-id="b3eac-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="b3eac-110">✔️ Użyj pól stałych dla stałych, które nigdy nie ulegną zmianie.</span><span class="sxs-lookup"><span data-stu-id="b3eac-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="b3eac-111">Kompilator pali wartości pól const bezpośrednio w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="b3eac-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="b3eac-112">W związku z tym nie można zmienić wartości stałych bez ryzyka naruszenia zgodności.</span><span class="sxs-lookup"><span data-stu-id="b3eac-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="b3eac-113">✔️ używać publicznych statycznych pól `readonly` dla wstępnie zdefiniowanych wystąpień obiektów.</span><span class="sxs-lookup"><span data-stu-id="b3eac-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="b3eac-114">Jeśli istnieją wstępnie zdefiniowane wystąpienia typu, zadeklaruj je jako publiczne pola statyczne tylko do odczytu samego typu.</span><span class="sxs-lookup"><span data-stu-id="b3eac-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="b3eac-115">❌ nie przypisuj wystąpień modyfikowalnych typów do pól `readonly`.</span><span class="sxs-lookup"><span data-stu-id="b3eac-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="b3eac-116">Typ modyfikowalny jest typem z wystąpieniami, które można zmodyfikować po utworzeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b3eac-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="b3eac-117">Na przykład tablice, większość kolekcji i strumienie są modyfikowalnymi typami, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>i <xref:System.String?displayProperty=nameWithType> są bardzo niezmienne.</span><span class="sxs-lookup"><span data-stu-id="b3eac-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="b3eac-118">Modyfikator tylko do odczytu w polu Typ odwołania zapobiega zastąpieniu wystąpienia w polu, ale nie zapobiega modyfikowaniu danych wystąpienia pola przez wywoływanie elementów członkowskich, które zmieniają wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b3eac-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="b3eac-119">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="b3eac-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b3eac-120">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="b3eac-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b3eac-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3eac-121">See also</span></span>

- [<span data-ttu-id="b3eac-122">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b3eac-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="b3eac-123">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="b3eac-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
