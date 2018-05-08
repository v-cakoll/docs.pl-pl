---
title: Właściwości zależności
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039015f895a491d8709815d6aff52eb6139d779f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-properties"></a>Właściwości zależności
Właściwości zależności (DP) jest regularne właściwość, która przechowuje wartość w magazynie właściwości zamiast magazynować je w zmiennej typu (pola), na przykład.  
  
 Właściwości dołączone zależności jest rodzajem modelowane jako statycznej metody Get i Set "właściwości" opisujące relacje między obiektami i ich kontenery reprezentujący właściwości zależności (np. pozycja `Button` obiekt na `Panel` kontener).  
  
 **CZY ✓** Podaj właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takie jak style, wyzwalaczy, wiązania z danymi, animacji, dynamicznych zasobów i dziedziczenia.  
  
## <a name="dependency-property-design"></a>Zależności właściwości projektu  
 **CZY ✓** dziedziczyć <xref:System.Windows.DependencyObject>, lub jeden z jego podtypach podczas implementowania właściwości zależności. Typ zawiera bardzo wydajny Implementacja magazynu właściwości i automatycznie obsługuje powiązanie danych WPF.  
  
 **CZY ✓** Podaj regularne właściwość CLR i publicznym statycznym polem tylko do odczytu przechowywania wystąpienia <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.  
  
 **CZY ✓** implementuje właściwości zależności przez wywołanie metody wystąpienia <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **CZY ✓** nazwę pola statycznego właściwości zależności suffixing nazwa właściwości z "Property".  
  
 **X nie** jawnie ustawić wartości domyślnych właściwości zależności w kodzie; ustawić je w metadanych.  
  
 Jeśli jawnie ustawione wartości domyślnej właściwości, może uniemożliwić ustawiany w sposób niejawny, takie jak style tej właściwości.  
  
 **X nie** umieść kod w akcesorach właściwości innych niż standardowe kodu można uzyskać dostępu do statycznego pola.  
  
 Kod nie będzie wykonanie jeśli właściwość jest ustawiona w sposób niejawny, stylów, np. ponieważ style używa pola statycznego bezpośrednio.  
  
 **X nie** zabezpieczać danych za pomocą właściwości zależności. Właściwości zależności nawet prywatne będą dostępne publicznie.  
  
## <a name="attached-dependency-property-design"></a>Zależności dołączonych właściwości projektu  
 Właściwości zależności opisane w poprzedniej sekcji reprezentują wewnętrzne właściwości typ deklarujący; na przykład `Text` właściwość jest właściwością `TextButton`, który deklaruje element. Specjalny rodzaj właściwość zależności jest właściwości dołączonych zależności.  
  
 Klasycznym przykład dołączona właściwość <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości. Właściwość reprezentuje pozycję w kolumnie przycisk (nie siatki), ale dotyczy on tylko jeśli przycisk jest zawarty w siatce, w związku z czym jest "dołączony" do przycisków przez siatki.  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 Definicja właściwości dołączonej wygląda przede wszystkim z właściwością zależności regularnych z tą różnicą, że metody dostępu są reprezentowane przez statycznej metody Get i Set:  
  
```  
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
  
## <a name="dependency-property-validation"></a>Sprawdzanie poprawności właściwości zależności  
 Właściwości wdrożenia często tak zwany sprawdzania poprawności. Logikę weryfikacji wykonuje podczas próby zmiany wartości właściwości.  
  
 Niestety metod dostępu do właściwości zależności nie mogą zawierać dowolny kod. Zamiast tego należy określić podczas rejestracji właściwości logikę weryfikacji właściwości zależności.  
  
 **X nie** umieść logikę sprawdzania poprawności właściwości zależności w akcesorach właściwości. Zamiast tego należy przekazać wywołanie zwrotne weryfikacji do `DependencyProperty.Register` metody.  
  
## <a name="dependency-property-change-notifications"></a>Powiadomienia o zmianie właściwości zależności  
 **X nie** zaimplementować Zmień logikę powiadomień w akcesorach właściwości zależności. Właściwości zależności mają wbudowane zmiany funkcji powiadomienia, używany podając wywołania zwrotnego powiadomienia zmiany do <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Koercja wartość właściwości zależności  
 Koercja właściwości ma miejsce, gdy wartość właściwości metody ustawiającej jest modyfikowany przez metodę ustawiającą, zanim Magazyn właściwości faktycznie jest modyfikowany.  
  
 **X nie** wdrożyć logikę koercja w akcesorach właściwości zależności.  
  
 Właściwości zależności dostępna jest funkcja wbudowana koercja i może służyć podając koercja wywołanie zwrotne do `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)
