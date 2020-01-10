---
title: Właściwości zależności
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709494"
---
# <a name="dependency-properties"></a>Właściwości zależności
Właściwość zależności (DP) to zwykła właściwość, która przechowuje jej wartość w magazynie właściwości, zamiast przechowywać ją w zmiennej typu (pole), na przykład.  
  
 Właściwość dołączona zależność jest rodzajem właściwości zależności modelowanym jako statyczne metody get i Set reprezentujące "właściwości" opisujące relacje między obiektami i ich kontenerami (np. położenie obiektu `Button` w kontenerze `Panel`).  
  
 **✓ DO** Podaj właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takie jak style, wyzwalaczy, wiązania z danymi, animacji, dynamicznych zasobów i dziedziczenia.  
  
## <a name="dependency-property-design"></a>Projekt właściwości zależności  
 **✓ DO** dziedziczyć <xref:System.Windows.DependencyObject>, lub jeden z jego podtypach podczas implementowania właściwości zależności. Typ zapewnia bardzo wydajną implementację magazynu właściwości i automatycznie obsługuje powiązanie danych WPF.  
  
 **✓ DO** Podaj regularne właściwość CLR i publicznym statycznym polem tylko do odczytu przechowywania wystąpienia <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.  
  
 **✓ DO** implementuje właściwości zależności przez wywołanie metody wystąpienia <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** nazwę pola statycznego właściwości zależności suffixing nazwa właściwości z "Property".  
  
 **X DO NOT** jawnie ustawić wartości domyślnych właściwości zależności w kodzie; ustawić je w metadanych.  
  
 Jeśli jawnie ustawisz właściwość domyślną, można zapobiec ustawianiu tej właściwości przez niejawne środki, takie jak style.  
  
 **X DO NOT** umieść kod w akcesorach właściwości innych niż standardowe kodu można uzyskać dostępu do statycznego pola.  
  
 Ten kod nie zostanie wykonany, jeśli właściwość jest ustawiona w sposób niejawny, na przykład w stylu, ponieważ style używa pola statycznego bezpośrednio.  
  
 **X DO NOT** zabezpieczać danych za pomocą właściwości zależności. Nawet prywatne właściwości zależności są dostępne publicznie.  
  
## <a name="attached-dependency-property-design"></a>Projekt właściwości dołączonej zależności  
 Właściwości zależności opisane w poprzedniej sekcji reprezentują właściwości wewnętrzne typu deklarującego; na przykład właściwość `Text` jest właściwością `TextButton`, która deklaruje ją. Szczególnym rodzajem właściwości zależności jest dołączona właściwość zależności.  
  
 Klasycznym przykładem dołączonej właściwości jest właściwość <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>. Właściwość reprezentuje położenie kolumny przycisku (nie siatki), ale ma zastosowanie tylko wtedy, gdy przycisk jest zawarty w siatce i dlatego jest "dołączony" do przycisków według siatki.  
  
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
  
 Definicja dołączonej właściwości wygląda głównie podobnie jak w przypadku właściwości zależności regularnej, z tą różnicą, że metody dostępu są reprezentowane za pomocą statycznych metod get i set:  
  
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
  
## <a name="dependency-property-validation"></a>Walidacja właściwości zależności  
 Właściwości często implementują to, co jest nazywane walidacją. Logika walidacji jest wykonywana, gdy podejmowana jest próba zmiany wartości właściwości.  
  
 Metody dostępu właściwości zależności nie mogą zawierać dowolnego kodu weryfikacyjnego. Zamiast tego należy określić logikę walidacji właściwości zależności podczas rejestracji właściwości.  
  
 **X DO NOT** umieść logikę sprawdzania poprawności właściwości zależności w akcesorach właściwości. Zamiast tego należy przekazać wywołanie zwrotne walidacji do metody `DependencyProperty.Register`.  
  
## <a name="dependency-property-change-notifications"></a>Powiadomienia o zmianie właściwości zależności  
 **X DO NOT** zaimplementować Zmień logikę powiadomień w akcesorach właściwości zależności. Właściwości zależności mają wbudowaną funkcję powiadomień o zmianach, która musi być używana przez dostarczenie wywołania zwrotnego powiadomienia o zmianie do <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Wymuszone przekształcenie wartości właściwości zależności  
 Wymuszanie właściwości odbywa się, gdy wartość określona dla metody ustawiającej właściwość jest modyfikowana przez metodę ustawiającą przed faktycznym zmodyfikowaniem magazynu właściwości.  
  
 **X DO NOT** wdrożyć logikę koercja w akcesorach właściwości zależności.  
  
 Właściwości zależności mają wbudowaną funkcję przymusu i mogą być używane przez dostarczenie wywołania zwrotnego przekształcenia do `PropertyMetadata`.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)
