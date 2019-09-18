---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053773"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="2ba02-102">x:FactoryMethod — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="2ba02-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="2ba02-103">Określa metodę inną niż Konstruktor, który powinien być używany przez procesor XAML do inicjowania obiektu po rozwiązaniu jego typu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="2ba02-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="2ba02-104">Użycie atrybutu języka XAML, brak X:arguments —</span><span class="sxs-lookup"><span data-stu-id="2ba02-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="2ba02-105">Użycie atrybutu języka XAML, X:arguments — jako elementy</span><span class="sxs-lookup"><span data-stu-id="2ba02-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="2ba02-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="2ba02-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="2ba02-107">Nazwa metody ciągu metody, którą procesory XAML wywołują w celu zainicjowania wystąpienia określonego jako `object`.</span><span class="sxs-lookup"><span data-stu-id="2ba02-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="2ba02-108">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="2ba02-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="2ba02-109">Co najmniej jeden element obiektu dla obiektów, które określają parametry metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="2ba02-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="2ba02-110">Kolejność jest istotna. oznacza kolejność, w jakiej argumenty powinny być przekazane do metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="2ba02-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ba02-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ba02-111">Remarks</span></span>  
 <span data-ttu-id="2ba02-112">Jeśli `methodname` jest to metoda wystąpienia, nie może być kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="2ba02-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="2ba02-113">Metody statyczne jako metody fabryki są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2ba02-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="2ba02-114">If `methodname` jest metodą statyczną, `methodname` jest podana jako *TypeName*. *kombinacja methodName* , gdzie *TypeName* nazywa klasę, która definiuje metodę dla fabryki statycznej.</span><span class="sxs-lookup"><span data-stu-id="2ba02-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="2ba02-115">*Właściwość TypeName* może być kwalifikowana przy użyciu prefiksu, jeśli odwołuje się do typu w zmapowanym xmlns.</span><span class="sxs-lookup"><span data-stu-id="2ba02-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="2ba02-116">Typ *TypeName* może być inny niż `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="2ba02-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="2ba02-117">Metoda fabryki musi być zadeklarowaną metodą publiczną typu, który wykonuje kopię zapasową odpowiedniego elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ba02-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="2ba02-118">Metoda fabryki musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ba02-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="2ba02-119">Metody fabryki nigdy nie powinny zwracać wartości null.</span><span class="sxs-lookup"><span data-stu-id="2ba02-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="2ba02-120">`x:Arguments`działa na zasadzie najlepszego dopasowania dla sygnatur metod fabryki.</span><span class="sxs-lookup"><span data-stu-id="2ba02-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="2ba02-121">Dopasowanie najpierw oblicza liczbę parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ba02-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="2ba02-122">Jeśli istnieje więcej niż jedno możliwe dopasowanie liczby parametrów, typ parametru jest następnie oceniany i jest określany optymalny odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="2ba02-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="2ba02-123">Jeśli po tej fazie oceny nadal występuje niejednoznaczność, zachowanie procesora XAML nie jest zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="2ba02-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="2ba02-124">Użycie `x:FactoryMethod` elementu nie jest użyciem elementu właściwości w typowym sensie, ponieważ znacznik dyrektywy nie odwołuje się do typu elementu obiektu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="2ba02-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="2ba02-125">Oczekuje się, że użycie elementu jest mniej typowe niż użycie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2ba02-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="2ba02-126">`x:Arguments`(użycie atrybutu lub elementu) może być używane razem z `x:FactoryMethod` użyciem elementu, ale nie jest to pokazane w sekcjach użycia.</span><span class="sxs-lookup"><span data-stu-id="2ba02-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="2ba02-127">`x:FactoryMethod`jako element musi poprzedzać wszystkie inne elementy właściwości, muszą poprzedzać `x:Arguments` wszelkie elementy, które również muszą poprzedzać dowolny tekst zawartości/wewnętrznego tekstu inicjującego.</span><span class="sxs-lookup"><span data-stu-id="2ba02-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba02-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ba02-128">See also</span></span>

- [<span data-ttu-id="2ba02-129">x:Arguments, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="2ba02-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
