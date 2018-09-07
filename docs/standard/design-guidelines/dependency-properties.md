---
title: Właściwości zależności
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c83dc75d1c86c89169fcc54220ced2a195bfbe
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079090"
---
# <a name="dependency-properties"></a>Właściwości zależności
Właściwości zależności (DP) jest regularne właściwość, która przechowuje wartość w magazynie właściwości zamiast przechowywania go w zmiennej typu (pola), na przykład.  
  
 Właściwości dołączone zależności jest rodzajem właściwość zależności modelowane jako statyczne metody Get i Set reprezentujący "właściwości" opisujące relacje między obiektami i ich kontenerów (np. położenie `Button` obiekt `Panel` kontener).  
  
 **✓ DO** Podaj właściwości zależności, jeśli potrzebujesz właściwości do obsługi funkcji WPF, takie jak style, wyzwalaczy, wiązania z danymi, animacji, dynamicznych zasobów i dziedziczenia.  
  
## <a name="dependency-property-design"></a>Projekt właściwości zależności  
 **✓ DO** dziedziczyć <xref:System.Windows.DependencyObject>, lub jeden z jego podtypach podczas implementowania właściwości zależności. Typ dostarcza implementację bardzo wydajny Magazyn właściwości i automatycznie obsługuje powiązanie danych WPF.  
  
 **✓ DO** Podaj regularne właściwość CLR i publicznym statycznym polem tylko do odczytu przechowywania wystąpienia <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> dla każdej właściwości zależności.  
  
 **✓ DO** implementuje właściwości zależności przez wywołanie metody wystąpienia <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> i <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** nazwę pola statycznego właściwości zależności suffixing nazwa właściwości z "Property".  
  
 **X DO NOT** jawnie ustawić wartości domyślnych właściwości zależności w kodzie; ustawić je w metadanych.  
  
 Jeśli jawnie ustawiono domyślną właściwość może uniemożliwić ustawiania w sposób niejawny, np. stylów tej właściwości.  
  
 **X DO NOT** umieść kod w akcesorach właściwości innych niż standardowe kodu można uzyskać dostępu do statycznego pola.  
  
 Kod nie będzie wykonanie jeśli właściwość jest ustawiona w sposób niejawny, np. stylów, ponieważ style bezpośrednio używa statycznego pola.  
  
 **X DO NOT** zabezpieczać danych za pomocą właściwości zależności. Właściwości zależności nawet prywatne są dostępne publicznie.  
  
## <a name="attached-dependency-property-design"></a>Zależność dołączonych właściwości projektu  
 Właściwości zależności opisane w poprzedniej sekcji reprezentują wewnętrzne właściwości typ deklarujący; na przykład `Text` właściwość jest właściwością `TextButton`, która deklaruje ją. Specjalny rodzaj właściwość zależności jest właściwość zależności dołączone.  
  
 Klasycznym przykładem dołączoną właściwość jest <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości. Właściwość reprezentuje pozycję w kolumnie przycisku (nie siatki), ale są tylko odpowiednie, jeśli przycisk znajduje się w siatce, więc jest "dołączony" przyciski przez siatki.  
  
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
  
 Definicja dołączoną właściwość wygląda przede wszystkim z właściwości zależności regularnych, z tą różnicą, że metody dostępu są reprezentowane przez statycznej metody Get i Set:  
  
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
  
## <a name="dependency-property-validation"></a>Weryfikacja właściwości zależności  
 Właściwości wdrożenia często tak zwany sprawdzania poprawności. Logikę weryfikacji wykonuje, gdy podejmowana jest próba zmiany wartości właściwości.  
  
 Niestety Akcesory właściwości zależności nie mogą zawierać dowolny kod. Logika sprawdzania poprawności właściwości zależności musi zostać określone podczas rejestracji właściwości.  
  
 **X DO NOT** umieść logikę sprawdzania poprawności właściwości zależności w akcesorach właściwości. Zamiast tego Przekaż wywołanie zwrotne weryfikacji, aby `DependencyProperty.Register` metody.  
  
## <a name="dependency-property-change-notifications"></a>Powiadomienia o zmianie właściwości zależności  
 **X DO NOT** zaimplementować Zmień logikę powiadomień w akcesorach właściwości zależności. Właściwości zależności mają zmiany wbudowanych funkcji powiadomienia, używany przez dostarczenie wywołania zwrotnego powiadomienia zmiany do <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Przekształcenie wartości właściwości zależności  
 Wymuszenia właściwość ma miejsce, gdy wartość właściwości metody ustawiającej jest modyfikowany przez metody ustawiającej, zanim Magazyn właściwości faktycznie jest modyfikowany.  
  
 **X DO NOT** wdrożyć logikę koercja w akcesorach właściwości zależności.  
  
 Właściwości zależności jest dostępna wbudowana wymuszenia i może służyć przez dostarczenie wywołanie zwrotne wymuszenia, aby `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Często używane wzorce projektowe](../../../docs/standard/design-guidelines/common-design-patterns.md)
