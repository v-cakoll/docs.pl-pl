---
title: Właściwości zależności
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866861"
---
# <a name="dependency-properties"></a><span data-ttu-id="f332c-102">Właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f332c-102">Dependency Properties</span></span>
<span data-ttu-id="f332c-103">Właściwości zależności (DP) jest regularne właściwość, która przechowuje wartość w magazynie właściwości zamiast przechowywania go w zmiennej typu (pola), na przykład.</span><span class="sxs-lookup"><span data-stu-id="f332c-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="f332c-104">Właściwości dołączone zależności jest rodzajem właściwość zależności modelowane jako statyczne metody Get i Set reprezentujący "właściwości" opisujące relacje między obiektami i ich kontenerów (np. położenie `Button` obiekt `Panel` kontener).</span><span class="sxs-lookup"><span data-stu-id="f332c-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="f332c-105">**✓ DO** Podaj właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takie jak style, wyzwalaczy, wiązania z danymi, animacji, dynamicznych zasobów i dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="f332c-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="f332c-106">Projekt właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f332c-106">Dependency Property Design</span></span>  
 <span data-ttu-id="f332c-107">**✓ DO** dziedziczyć <xref:System.Windows.DependencyObject>, lub jeden z jego podtypach podczas implementowania właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f332c-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="f332c-108">Typ dostarcza implementację bardzo wydajny Magazyn właściwości i automatycznie obsługuje powiązanie danych WPF.</span><span class="sxs-lookup"><span data-stu-id="f332c-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="f332c-109">**✓ DO** Podaj regularne właściwość CLR i publicznym statycznym polem tylko do odczytu przechowywania wystąpienia <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f332c-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="f332c-110">**✓ DO** implementuje właściwości zależności przez wywołanie metody wystąpienia <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f332c-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f332c-111">**✓ DO** nazwę pola statycznego właściwości zależności suffixing nazwa właściwości z "Property".</span><span class="sxs-lookup"><span data-stu-id="f332c-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="f332c-112">**X DO NOT** jawnie ustawić wartości domyślnych właściwości zależności w kodzie; ustawić je w metadanych.</span><span class="sxs-lookup"><span data-stu-id="f332c-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="f332c-113">Jeśli jawnie ustawiono domyślną właściwość może uniemożliwić ustawiania w sposób niejawny, np. stylów tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f332c-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="f332c-114">**X DO NOT** umieść kod w akcesorach właściwości innych niż standardowe kodu można uzyskać dostępu do statycznego pola.</span><span class="sxs-lookup"><span data-stu-id="f332c-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="f332c-115">Kod nie będzie wykonanie jeśli właściwość jest ustawiona w sposób niejawny, np. stylów, ponieważ style bezpośrednio używa statycznego pola.</span><span class="sxs-lookup"><span data-stu-id="f332c-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="f332c-116">**X DO NOT** zabezpieczać danych za pomocą właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f332c-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="f332c-117">Właściwości zależności nawet prywatne są dostępne publicznie.</span><span class="sxs-lookup"><span data-stu-id="f332c-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="f332c-118">Zależność dołączonych właściwości projektu</span><span class="sxs-lookup"><span data-stu-id="f332c-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="f332c-119">Właściwości zależności opisane w poprzedniej sekcji reprezentują wewnętrzne właściwości typ deklarujący; na przykład `Text` właściwość jest właściwością `TextButton`, która deklaruje ją.</span><span class="sxs-lookup"><span data-stu-id="f332c-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="f332c-120">Specjalny rodzaj właściwość zależności jest właściwość zależności dołączone.</span><span class="sxs-lookup"><span data-stu-id="f332c-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="f332c-121">Klasycznym przykładem dołączoną właściwość jest <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f332c-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f332c-122">Właściwość reprezentuje pozycję w kolumnie przycisku (nie siatki), ale są tylko odpowiednie, jeśli przycisk znajduje się w siatce, więc jest "dołączony" przyciski przez siatki.</span><span class="sxs-lookup"><span data-stu-id="f332c-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 <span data-ttu-id="f332c-123">Definicja dołączoną właściwość wygląda przede wszystkim z właściwości zależności regularnych, z tą różnicą, że metody dostępu są reprezentowane przez statycznej metody Get i Set:</span><span class="sxs-lookup"><span data-stu-id="f332c-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a><span data-ttu-id="f332c-124">Weryfikacja właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f332c-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="f332c-125">Właściwości wdrożenia często tak zwany sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f332c-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="f332c-126">Logikę weryfikacji wykonuje, gdy podejmowana jest próba zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="f332c-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="f332c-127">Niestety Akcesory właściwości zależności nie mogą zawierać dowolny kod.</span><span class="sxs-lookup"><span data-stu-id="f332c-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="f332c-128">Logika sprawdzania poprawności właściwości zależności musi zostać określone podczas rejestracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="f332c-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="f332c-129">**X DO NOT** umieść logikę sprawdzania poprawności właściwości zależności w akcesorach właściwości.</span><span class="sxs-lookup"><span data-stu-id="f332c-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="f332c-130">Zamiast tego Przekaż wywołanie zwrotne weryfikacji, aby `DependencyProperty.Register` metody.</span><span class="sxs-lookup"><span data-stu-id="f332c-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="f332c-131">Powiadomienia o zmianie właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f332c-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="f332c-132">**X DO NOT** zaimplementować Zmień logikę powiadomień w akcesorach właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f332c-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="f332c-133">Właściwości zależności mają zmiany wbudowanych funkcji powiadomienia, używany przez dostarczenie wywołania zwrotnego powiadomienia zmiany do <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="f332c-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="f332c-134">Przekształcenie wartości właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="f332c-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="f332c-135">Wymuszenia właściwość ma miejsce, gdy wartość właściwości metody ustawiającej jest modyfikowany przez metody ustawiającej, zanim Magazyn właściwości faktycznie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="f332c-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="f332c-136">**X DO NOT** wdrożyć logikę koercja w akcesorach właściwości zależności.</span><span class="sxs-lookup"><span data-stu-id="f332c-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="f332c-137">Właściwości zależności jest dostępna wbudowana wymuszenia i może służyć przez dostarczenie wywołanie zwrotne wymuszenia, aby `PropertyMetadata`.</span><span class="sxs-lookup"><span data-stu-id="f332c-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="f332c-138">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f332c-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f332c-139">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="f332c-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f332c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f332c-140">See also</span></span>

- [<span data-ttu-id="f332c-141">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f332c-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="f332c-142">Często używane wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="f332c-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
