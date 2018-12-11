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
author: KrzysztofCwalina
ms.openlocfilehash: 240492590fab4579b9d984d5dce759f6d9f8cbab
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153114"
---
# <a name="struct-design"></a><span data-ttu-id="1e5c8-102">Projekt struktury</span><span class="sxs-lookup"><span data-stu-id="1e5c8-102">Struct Design</span></span>
<span data-ttu-id="1e5c8-103">Typ wartości ogólnego przeznaczenia najczęściej nazywa się struktury, jego słowo kluczowe języka C#.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="1e5c8-104">Ta sekcja zawiera wskazówki dotyczące projektowania struktury ogólne.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="1e5c8-105">**X DO NOT** Podaj domyślnego konstruktora dla struktury.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="1e5c8-106">Ta wytyczna następujące umożliwia tablic struktur, które ma zostać utworzony bez konieczności uruchamiania konstruktora dla każdego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="1e5c8-107">Należy zauważyć, że języka C# nie zezwala na struktur ma domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="1e5c8-108">**X DO NOT** Definiowanie typów modyfikowalne wartości.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="1e5c8-109">Typy wartości modyfikowalne ma kilka problemów.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-109">Mutable value types have several problems.</span></span> <span data-ttu-id="1e5c8-110">Na przykład gdy pobierającą właściwość zwraca typ wartości, obiekt wywołujący otrzymuje kopię.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="1e5c8-111">Ponieważ kopia zostanie utworzona w sposób niejawny, deweloperzy może nie być pamiętać, że są mutacja kopii i nie oryginalną wartość.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="1e5c8-112">Ponadto niektóre języki (dynamiczna języków, w szczególności) występują problemy przy użyciu typów wartości modyfikowalne, ponieważ zmienne lokalne, nawet wtedy, gdy wyłuskany, spowodować kopię ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="1e5c8-113">**✓ DO** zapewnić, że stan, w którym wszystkie dane wystąpienia jest ustawiony na zero, wartość false lub wartość null (zgodnie z potrzebami) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="1e5c8-114">Zapobiega to przypadkowym tworzenia nieprawidłowe wystąpień, po utworzeniu tablicy struktur.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="1e5c8-115">**✓ DO** zaimplementować <xref:System.IEquatable%601> w typach wartości.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="1e5c8-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Metody w typach wartości powoduje, że konwersja boxing i jego domyślna implementacja jest bardzo wydajny, ponieważ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="1e5c8-117"><xref:System.IEquatable%601.Equals%2A> może być znacznie lepszej wydajności, a następnie można zaimplementować tak, aby nie spowoduje pakowania.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="1e5c8-118">**X DO NOT** jawnie rozszerzyć <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="1e5c8-119">W rzeczywistości większość języków temu zapobiec.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="1e5c8-120">Ogólnie rzecz biorąc struktury mogą być bardzo przydatne, ale należy używać tylko małej, pojedynczej, niezmienne wartości, które nie zostać opakowany często.</span><span class="sxs-lookup"><span data-stu-id="1e5c8-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="1e5c8-121">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="1e5c8-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1e5c8-122">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="1e5c8-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5c8-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e5c8-123">See also</span></span>

- [<span data-ttu-id="1e5c8-124">Typy — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1e5c8-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="1e5c8-125">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1e5c8-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="1e5c8-126">Wybieranie między klasą i strukturą</span><span class="sxs-lookup"><span data-stu-id="1e5c8-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
