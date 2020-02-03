---
title: Projekt struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: b6d06bc8a1e8535f1452af0726138abaebfd4951
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743612"
---
# <a name="struct-design"></a><span data-ttu-id="8b22b-102">Projekt struktury</span><span class="sxs-lookup"><span data-stu-id="8b22b-102">Struct Design</span></span>
<span data-ttu-id="8b22b-103">Typ wartości ogólnego przeznaczenia jest najczęściej określany jako struktura, jego C# słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8b22b-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="8b22b-104">Ta sekcja zawiera wskazówki dotyczące ogólnego projektowania struktury.</span><span class="sxs-lookup"><span data-stu-id="8b22b-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="8b22b-105">❌ nie udostępniaj konstruktora bez parametrów dla struktury.</span><span class="sxs-lookup"><span data-stu-id="8b22b-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="8b22b-106">Poniższe wytyczne umożliwiają tworzenie tablic struktur bez konieczności uruchamiania konstruktora dla każdego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="8b22b-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="8b22b-107">Zwróć uwagę C# , że struktury nie umożliwiają konstruktorom bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="8b22b-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="8b22b-108">❌ nie definiować modyfikowalnych typów wartościowych.</span><span class="sxs-lookup"><span data-stu-id="8b22b-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="8b22b-109">Modyfikowalne typy wartości mają kilka problemów.</span><span class="sxs-lookup"><span data-stu-id="8b22b-109">Mutable value types have several problems.</span></span> <span data-ttu-id="8b22b-110">Na przykład, gdy metoda pobierająca Właściwość zwraca typ wartości, wywołujący otrzymuje kopię.</span><span class="sxs-lookup"><span data-stu-id="8b22b-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="8b22b-111">Ponieważ kopia jest tworzona niejawnie, deweloperzy mogą nie wiedzieć, że są one mutacją, a nie pierwotną wartością.</span><span class="sxs-lookup"><span data-stu-id="8b22b-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="8b22b-112">Ponadto w niektórych językach (w szczególności Języki dynamiczne) występują problemy z użyciem modyfikowalnych typów wartości, ponieważ nawet zmienne lokalne, gdy jest używana, powoduje, że kopia zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="8b22b-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="8b22b-113">✔️ Upewnij się, że stan, w którym wszystkie dane wystąpienia są ustawione na wartość zero, wartość false lub wartość null (odpowiednio), jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8b22b-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="8b22b-114">Zapobiega to przypadkowemu tworzeniu nieprawidłowych wystąpień podczas tworzenia tablicy struktur.</span><span class="sxs-lookup"><span data-stu-id="8b22b-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="8b22b-115">✔️ Implementowanie <xref:System.IEquatable%601> na typach wartości.</span><span class="sxs-lookup"><span data-stu-id="8b22b-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="8b22b-116">Metoda <xref:System.Object.Equals%2A?displayProperty=nameWithType> w typach wartości powoduje opakowanie, a jej domyślna implementacja nie jest bardzo wydajna, ponieważ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="8b22b-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="8b22b-117"><xref:System.IEquatable%601.Equals%2A> może mieć znacznie lepszą wydajność i można ją zaimplementować, aby nie powodowały pakowania.</span><span class="sxs-lookup"><span data-stu-id="8b22b-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="8b22b-118">niejawnie rozszerzona <xref:System.ValueType>❌.</span><span class="sxs-lookup"><span data-stu-id="8b22b-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="8b22b-119">W rzeczywistości większość języków zapobiega tym.</span><span class="sxs-lookup"><span data-stu-id="8b22b-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="8b22b-120">Ogólnie rzecz biorąc, struktury mogą być bardzo przydatne, ale powinny być używane tylko w przypadku małych, pojedynczych, niezmiennych wartości, które nie będą często opakowane.</span><span class="sxs-lookup"><span data-stu-id="8b22b-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="8b22b-121">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="8b22b-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8b22b-122">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="8b22b-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8b22b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b22b-123">See also</span></span>

- [<span data-ttu-id="8b22b-124">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="8b22b-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="8b22b-125">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="8b22b-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8b22b-126">Wybieranie między klasą i strukturą</span><span class="sxs-lookup"><span data-stu-id="8b22b-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
