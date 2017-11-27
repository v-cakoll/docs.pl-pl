---
title: "x:FactoryMethod — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 0d53db49961c2a75e4547f6b57240cefd2cc17c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="9ed7e-102">x:FactoryMethod — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="9ed7e-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="9ed7e-103">Określa metodę innego niż konstruktor, który procesor XAML powinna być używana do zainicjowania obiektu po rozwiązaniu jego typ zapasowy.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="9ed7e-104">Użycie atrybutu XAML, x: Arguments</span><span class="sxs-lookup"><span data-stu-id="9ed7e-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="9ed7e-105">Użycie atrybutu XAML, x: Arguments jako elementów:</span><span class="sxs-lookup"><span data-stu-id="9ed7e-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9ed7e-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="9ed7e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="9ed7e-107">Nazwa metody ciąg metody, która procesorów XAML wywołania do inicjowania wystąpienia określony jako `object`.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="9ed7e-108">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="9ed7e-109">Co najmniej jeden element obiektu dla obiektów, które parametry metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="9ed7e-110">Kolejność jest znacząca; oznacza on, kolejność, w którym argumenty powinny zostać przekazane do metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed7e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ed7e-111">Remarks</span></span>  
 <span data-ttu-id="9ed7e-112">Jeśli `methodname` jest metodą wystąpienia nie może być kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="9ed7e-113">Metody statycznej metody fabryki są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="9ed7e-114">Jeśli `methodname` jest metodą statyczną `methodname` jest dostarczane jako *typeName*. *methodName* razem, gdy *typeName* nazwy klasy, która definiuje metody statycznej fabryki.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="9ed7e-115">*właściwość typeName* może być prefiks kwalifikowana Jeśli odwołuje się do typu w mapowanej xmlns.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="9ed7e-116">*właściwość typeName* może być innego typu niż `typeof(``object``)`.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="9ed7e-117">Metoda fabryki musi być zadeklarowany publiczną metodę typu, aby utworzyć kopię zapasową elementu odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="9ed7e-118">Metoda fabryki musi zwracać wystąpienie, które można przypisać do odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="9ed7e-119">Metody fabryki nigdy nie powinien zwrócić wartość null.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="9ed7e-120">`x:Arguments`działa na zasadzie najlepszego dopasowania dla sygnatury metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="9ed7e-121">Dopasowywanie oblicza najpierw liczba parametrów.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="9ed7e-122">Jeśli istnieje więcej niż jedno dopasowanie możliwe w dla liczby parametrów, typ parametru jest obliczane i najlepsze dopasowanie jest określana.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="9ed7e-123">Jeśli po tym etapie oceny nadal jest niejednoznaczności, zachowanie procesora XAML jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="9ed7e-124">`x:FactoryMethod` Użycie elementu nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znacznika dyrektywy nie odwołuje się do typu zawierającego element object.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="9ed7e-125">Oczekuje się użycie tego elementu jest mniej typowych niż użycie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="9ed7e-126">`x:Arguments`(użycie atrybutu lub elementu) może być używany wraz z `x:FactoryMethod` użycie elementu, ale nie jest specjalnie widoczne w sekcji użycia.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="9ed7e-127">`x:FactoryMethod`jako element musi poprzedzać wszystkie inne elementy właściwości, należy poprzedzić żadnego `x:Arguments` również dostarczane jako elementy i musi poprzedzać tekst zawartości/wewnętrzny tekst/inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9ed7e-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed7e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ed7e-128">See Also</span></span>  
 [<span data-ttu-id="9ed7e-129">x: Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="9ed7e-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
