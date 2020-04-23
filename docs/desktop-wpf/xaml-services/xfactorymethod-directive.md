---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071536"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="6df29-102">x:FactoryMethod — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="6df29-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="6df29-103">Określa metodę inną niż konstruktor, której procesor XAML powinien używać do inicjowania obiektu po rozwiązaniu jego typu kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="6df29-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="6df29-104">Użycie atrybutu XAML, brak argumentów x:Argumenty</span><span class="sxs-lookup"><span data-stu-id="6df29-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="6df29-105">Użycie atrybutu XAML, x:Argumenty jako elementy</span><span class="sxs-lookup"><span data-stu-id="6df29-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6df29-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="6df29-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="6df29-107">Nazwa metody ciągu metody wywoływanej przez procesory XAML w `object`celu zainicjowania wystąpienia określonego jako .</span><span class="sxs-lookup"><span data-stu-id="6df29-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="6df29-108">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="6df29-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="6df29-109">Jeden lub więcej elementów obiektu dla obiektów, które określają parametry metody fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="6df29-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="6df29-110">Kolejność jest znacząca; oznacza kolejność, w jakiej argumenty powinny być przekazywane do metody fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="6df29-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6df29-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6df29-111">Remarks</span></span>  
 <span data-ttu-id="6df29-112">Jeśli `methodname` jest to metoda wystąpienia, nie można jej zakwalifikować.</span><span class="sxs-lookup"><span data-stu-id="6df29-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="6df29-113">Obsługiwane są metody statyczne jako metody fabryczne.</span><span class="sxs-lookup"><span data-stu-id="6df29-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="6df29-114">Jeśli `methodname` jest metodą `methodname` statyczną, `typeName.methodName` jest dostarczana jako kombinacja, gdzie `typeName` nazwy klasy, która definiuje statyczną metodę fabryczną.</span><span class="sxs-lookup"><span data-stu-id="6df29-114">If `methodname` is a static method, `methodname` is provided as a `typeName.methodName` combination, where `typeName` names the class that defines the static factory method.</span></span> <span data-ttu-id="6df29-115">`typeName`może być kwalifikowany prefiksem, jeśli odnosi się do typu w mapowanych xmlns.</span><span class="sxs-lookup"><span data-stu-id="6df29-115">`typeName` can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="6df29-116">`typeName`może być inny `typeof(object)`typ niż .</span><span class="sxs-lookup"><span data-stu-id="6df29-116">`typeName` can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="6df29-117">Metoda fabryczna musi być zadeklarowaną metodą publiczną typu, która cofa odpowiedni element obiektu.</span><span class="sxs-lookup"><span data-stu-id="6df29-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="6df29-118">Metoda fabryczna musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6df29-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="6df29-119">Metody fabryczne nigdy nie powinny zwracać wartości null.</span><span class="sxs-lookup"><span data-stu-id="6df29-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="6df29-120">`x:Arguments`działa na zasadzie najlepszego dopasowania do podpisów metod fabrycznych.</span><span class="sxs-lookup"><span data-stu-id="6df29-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="6df29-121">Dopasowanie najpierw ocenia liczbę parametrów.</span><span class="sxs-lookup"><span data-stu-id="6df29-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="6df29-122">Jeśli istnieje więcej niż jedno możliwe dopasowanie dla liczby parametrów, typ parametru jest następnie oceniany i określa się najlepsze dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="6df29-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="6df29-123">Jeśli po tej fazie oceny nadal występują niejednoznaczności, zachowanie procesora XAML jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="6df29-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="6df29-124">Użycie `x:FactoryMethod` elementu nie jest użycie elementu właściwości w typowym sensie, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu zawierającego obiekt.</span><span class="sxs-lookup"><span data-stu-id="6df29-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="6df29-125">Oczekuje się, że użycie elementu jest mniej powszechne niż użycie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6df29-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="6df29-126">`x:Arguments`(użycie atrybutu lub elementu) może być `x:FactoryMethod` używany wraz z użyciem elementu, ale nie jest to wyraźnie pokazane w sekcjach Użycie.</span><span class="sxs-lookup"><span data-stu-id="6df29-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="6df29-127">`x:FactoryMethod`jako element musi poprzedzać wszelkie inne elementy `x:Arguments` właściwości, musi poprzedzać wszelkie również jako elementy i musi poprzedzać wszelkie content/tekst wewnętrzny/tekst inicjujący.</span><span class="sxs-lookup"><span data-stu-id="6df29-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df29-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6df29-128">See also</span></span>

- [<span data-ttu-id="6df29-129">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="6df29-129">x:Arguments Directive</span></span>](xarguments-directive.md)
