---
title: Projektowanie struktury
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a><span data-ttu-id="0eb37-102">Projektowanie struktury</span><span class="sxs-lookup"><span data-stu-id="0eb37-102">Struct Design</span></span>
<span data-ttu-id="0eb37-103">Typ wartości ogólnego przeznaczenia najczęściej nazywa się struktury, jego słowo kluczowe języka C#.</span><span class="sxs-lookup"><span data-stu-id="0eb37-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="0eb37-104">Ta sekcja zawiera wskazówki dotyczące projektowania struktury ogólne.</span><span class="sxs-lookup"><span data-stu-id="0eb37-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="0eb37-105">**X nie** Podaj domyślnego konstruktora dla struktury.</span><span class="sxs-lookup"><span data-stu-id="0eb37-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="0eb37-106">Niniejsze wytyczne po umożliwia tablice struktur ma zostać utworzony bez konieczności uruchamiania Konstruktora na każdy element tablicy.</span><span class="sxs-lookup"><span data-stu-id="0eb37-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="0eb37-107">Zwróć uwagę, że C# nie zezwala na struktury ma domyślnych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="0eb37-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="0eb37-108">**X nie** Definiowanie typów modyfikowalne wartości.</span><span class="sxs-lookup"><span data-stu-id="0eb37-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="0eb37-109">Typy wartości modyfikowalne ma kilka problemów.</span><span class="sxs-lookup"><span data-stu-id="0eb37-109">Mutable value types have several problems.</span></span> <span data-ttu-id="0eb37-110">Na przykład gdy metody pobierającej właściwość zwraca typ wartości, wywołujący wysyłana kopia.</span><span class="sxs-lookup"><span data-stu-id="0eb37-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="0eb37-111">Ponieważ kopia zostanie utworzona niejawnie, deweloperzy mogą nie być pamiętać, że są mutacja kopia i nie oryginalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="0eb37-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="0eb37-112">Ponadto w przypadku niektórych języków (dynamiczny języki, w szczególności) występują problemy przy użyciu typów wartości modyfikowalne, ponieważ nawet zmiennych lokalnych, gdy wyłuskiwany, spowodować kopii ma zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="0eb37-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="0eb37-113">**CZY ✓** zapewnić, że stan, w którym wszystkie dane wystąpienia jest ustawiony na zero, wartość false lub wartość null (zgodnie z potrzebami) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="0eb37-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="0eb37-114">Zapobiega przypadkowemu tworzenia wystąpień nieprawidłowy, po utworzeniu tablicę struktury.</span><span class="sxs-lookup"><span data-stu-id="0eb37-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="0eb37-115">**CZY ✓** zaimplementować <xref:System.IEquatable%601> w typach wartości.</span><span class="sxs-lookup"><span data-stu-id="0eb37-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="0eb37-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType> Metody w typach wartości powoduje, że opakowywanie i jego domyślna implementacja nie jest bardzo wydajny, ponieważ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="0eb37-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="0eb37-117"><xref:System.IEquatable%601.Equals%2A>może być znacznie lepszą wydajność i można zaimplementować tak, aby nie spowoduje boxing.</span><span class="sxs-lookup"><span data-stu-id="0eb37-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="0eb37-118">**X nie** jawnie rozszerzyć <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="0eb37-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="0eb37-119">W rzeczywistości większość języków temu zapobiec.</span><span class="sxs-lookup"><span data-stu-id="0eb37-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="0eb37-120">Ogólnie rzecz biorąc struktury może być bardzo przydatne, ale należy używać tylko w małych, jednego, modyfikować wartości, które nie można spakować często.</span><span class="sxs-lookup"><span data-stu-id="0eb37-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="0eb37-121">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="0eb37-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0eb37-122">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="0eb37-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb37-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0eb37-123">See Also</span></span>  
 [<span data-ttu-id="0eb37-124">Wytyczne dotyczące projektowania typu</span><span class="sxs-lookup"><span data-stu-id="0eb37-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="0eb37-125">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="0eb37-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0eb37-126">Wybór między klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="0eb37-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
