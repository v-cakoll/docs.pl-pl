---
title: x:FactoryMethod — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 8fff4d62e07bdfd4ecc27d2692c391251afdd6d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190694"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="66558-102">x:FactoryMethod — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="66558-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="66558-103">Określa metody innej niż konstruktora, który procesor XAML powinna być używana do inicjowania obiektu po rozwiązaniu jego zapasowego typu.</span><span class="sxs-lookup"><span data-stu-id="66558-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="66558-104">Użycie atrybutu XAML, x: Arguments</span><span class="sxs-lookup"><span data-stu-id="66558-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="66558-105">Użycie atrybutu XAML, x: Arguments, jako elementów:</span><span class="sxs-lookup"><span data-stu-id="66558-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="66558-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="66558-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="66558-107">Nazwa metody parametry metody, która procesorów XAML wywołania do inicjowania wystąpienia określony jako `object`.</span><span class="sxs-lookup"><span data-stu-id="66558-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="66558-108">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="66558-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="66558-109">Co najmniej jeden element obiektu dla obiektów, które określają parametry metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="66558-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="66558-110">Kolejność jest znacząca; oznacza kolejność, w której argumenty powinien zostać przekazany do metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="66558-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66558-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66558-111">Remarks</span></span>  
 <span data-ttu-id="66558-112">Jeśli `methodname` jest metodą wystąpienia nie może być kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="66558-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="66558-113">Metody statyczne służące jako metodami factory są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="66558-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="66558-114">Jeśli `methodname` jest statycznej metody `methodname` jest dostarczana jako *typeName*. *methodName* kombinacji, gdzie *typeName* nazwy klasy, która definiuje metody statyczne fabryki.</span><span class="sxs-lookup"><span data-stu-id="66558-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="66558-115">*Element typeName* może być prefiksem kwalifikowanego Jeśli odwołujące się do typu w mapowanych xmlns.</span><span class="sxs-lookup"><span data-stu-id="66558-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="66558-116">*Element typeName* może być typ inny niż `typeof(object)`.</span><span class="sxs-lookup"><span data-stu-id="66558-116">*typeName* can be a different type than `typeof(object)`.</span></span>  
  
 <span data-ttu-id="66558-117">Metoda fabryki musi być zadeklarowany publiczną metodę typu, która będzie tworzyć kopię elementu odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="66558-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="66558-118">Metoda fabryki musi zwrócić wystąpienie, które można przypisać do odpowiedniego obiektu.</span><span class="sxs-lookup"><span data-stu-id="66558-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="66558-119">Metodami Factory nigdy nie powinna zwracać wartość null.</span><span class="sxs-lookup"><span data-stu-id="66558-119">Factory methods should never return null.</span></span>  
  
 `x:Arguments` <span data-ttu-id="66558-120">działa na zasadzie najlepiej dopasowana podpisy metod fabryki.</span><span class="sxs-lookup"><span data-stu-id="66558-120">operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="66558-121">Dopasowywanie najpierw sprawdza liczba parametrów.</span><span class="sxs-lookup"><span data-stu-id="66558-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="66558-122">Jeśli istnieje więcej niż jeden odpowiadającego liczba parametrów, typ parametru jest następnie oceniany i najlepsze dopasowanie jest określana.</span><span class="sxs-lookup"><span data-stu-id="66558-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="66558-123">Jeśli po tym etapie oceny nadal jest niejednoznaczności, XAML procesora zachowanie jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="66558-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="66558-124">`x:FactoryMethod` Użycie elementu nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="66558-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="66558-125">Oczekuje się, że użycie elementu jest rzadziej niż użycie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="66558-125">It is expected that element usage is less common than attribute usage.</span></span> `x:Arguments` <span data-ttu-id="66558-126">(użycie atrybutu lub elementu) może być używana wraz z `x:FactoryMethod` użycie elementu, ale nie jest specjalnie wyświetlany w sekcji użycia.</span><span class="sxs-lookup"><span data-stu-id="66558-126">(either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 `x:FactoryMethod` <span data-ttu-id="66558-127">jako element musi poprzedzać wszystkie inne elementy właściwości, należy poprzedzić dowolne `x:Arguments` również dostarczane jako elementy, a musi poprzedzać dowolny tekst zawartości/wewnętrzny tekst/inicjowania.</span><span class="sxs-lookup"><span data-stu-id="66558-127">as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66558-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66558-128">See also</span></span>

- [<span data-ttu-id="66558-129">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="66558-129">x:Arguments Directive</span></span>](x-arguments-directive.md)
