---
title: Atrybuty wspólne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5bc568279a6952fdc5e0a000b1208cd7f9cfd6e7
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524284"
---
# <a name="common-attributes-visual-basic"></a>Atrybuty wspólne (Visual Basic)

W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.

- [Atrybuty globalne](#Global)

- [Przestarzały atrybut](#Obsolete)

- [Atrybut warunkowy](#Conditional)

- [Atrybuty informacji o wywołującym](#CallerInfo)

- [Atrybuty Visual Basic](#VB)

## <a name="Global"></a>Atrybuty globalne

Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu. Na przykład atrybut <xref:System.Reflection.AssemblyVersionAttribute> może służyć do osadzania informacji o wersji w zestawie, takich jak:

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

Atrybuty globalne pojawiają się w kodzie źródłowym po każdej instrukcji `Imports` najwyższego poziomu i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw. Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji. W przypadku projektów Visual Basic atrybuty globalne są zwykle umieszczane w pliku AssemblyInfo. vb (plik jest tworzony automatycznie podczas tworzenia projektu w programie Visual Studio).

Atrybuty zestawu są wartościami, które zawierają informacje o zestawie. Należą do następujących kategorii:

- Atrybuty tożsamości zestawu

- Atrybuty informacyjne

- Atrybuty manifestu zestawu

### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu

Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie. Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów. Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu. Atrybut <xref:System.Reflection.AssemblyFlagsAttribute> określa, czy wiele kopii zestawu może współistnieć.

W poniższej tabeli przedstawiono atrybuty tożsamości.

|Atrybut|Cel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|W pełni opisuje tożsamość zestawu.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa kulturę obsługiwaną przez zestaw.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|

### <a name="informational-attributes"></a>Atrybuty informacyjne

Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w przestrzeni nazw <xref:System.Reflection?displayProperty=nameWithType>.

|Atrybut|Cel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Definiuje niestandardowy atrybut, który określa nazwę produktu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definiuje niestandardowy atrybut, który określa znak towarowy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definiuje niestandardowy atrybut, który określa wersję informacyjną dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definiuje niestandardowy atrybut, który określa nazwę firmy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definiuje niestandardowy atrybut, który określa prawo autorskie dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilator, aby używał określonego numeru wersji dla zasobu wersji plików Win32.|
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).|

### <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu

Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu. Obejmuje to tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w przestrzeni nazw <xref:System.Reflection?displayProperty=nameWithType>.

|Atrybut|Cel|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje przyjazny alias domyślny dla manifestu zestawu|

## <a name="Obsolete"></a>Przestarzały atrybut

Atrybut `Obsolete` oznacza jednostkę programu, która nie jest już zalecana do użycia. Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu. Na przykład:

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

W tym przykładzie atrybut `Obsolete` jest stosowany do klasy `A` i do metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu zastosowany do `B.OldMethod` jest ustawiony na `true`, ta metoda spowoduje błąd kompilatora, natomiast użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia. Wywołanie `B.NewMethod`, jednak nie powoduje ostrzeżenia ani błędu.

Ciąg dostarczony jako pierwszy argument konstruktora atrybutu będzie wyświetlany jako część ostrzeżenia lub błędu. Na przykład jeśli używasz go z poprzednimi definicjami, poniższy kod generuje dwie ostrzeżenia i jeden błąd:

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

Wygenerowane są dwa ostrzeżenia dla `A` klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy.

Atrybut `Obsolete` może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.

Atrybut `Obsolete` jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty. `Obsolete` jest aliasem <xref:System.ObsoleteAttribute>.

## <a name="Conditional"></a>Atrybut warunkowy

Atrybut `Conditional` wykonuje metodę zależną od identyfikatora przetwarzania wstępnego. Atrybut `Conditional` jest aliasem dla <xref:System.Diagnostics.ConditionalAttribute> i może być zastosowany do metody lub klasy atrybutu.

W tym przykładzie `Conditional` jest stosowana do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:

```vb
#Const TRACE_ON = True
Imports System
Imports System.Diagnostics
Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

Jeśli identyfikator `TRACE_ON` nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.

Atrybut `Conditional` jest często używany z identyfikatorem `DEBUG` do włączania funkcji śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydań, takich jak:

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte. Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte. Używanie `Conditional` jest oczyszczarką, bardziej eleganckim i mniej podatnym na błędy alternatywą dla otaczających metod w blokach `#if…#endif`, takich jak:

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.

### <a name="using-multiple-identifiers"></a>Używanie wielu identyfikatorów

Jeśli metoda ma wiele atrybutów `Conditional`, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR). W tym przykładzie obecność `A` lub `B` spowoduje wywołanie metody:

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe. Przykładowo druga metoda zostanie wykonana tylko wtedy, gdy zdefiniowano zarówno `A`, jak i `B`:

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a>Używanie warunkowe z klasami atrybutów

Atrybut `Conditional` można również zastosować do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="CallerInfo"></a>Atrybuty informacji o wywołującym

Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.

Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy opcjonalny parametr określa wartość domyślną. W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:

|Atrybut|Opis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub nazwa właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|

Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).

## <a name="VB"></a>Atrybuty Visual Basic

W poniższej tabeli wymieniono atrybuty, które są specyficzne dla Visual Basic.

|Atrybut|Cel|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Wskazuje kompilatorowi, że klasa powinna być udostępniana jako obiekt COM.|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Zezwala na dostęp do elementów członkowskich modułu wyłącznie przy użyciu kwalifikacji wymaganych dla modułu.|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Określa rozmiar ciągu o stałej długości w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Określa rozmiar stałej tablicy w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.|

### <a name="comclassattribute"></a>COMClassAttribute

Użyj `COMClassAttribute`, aby uprościć proces tworzenia składników modelu COM z Visual Basic. Obiekty COM różnią się znacznie od zestawów .NET Framework i nie `COMClassAttribute`, należy wykonać kilka czynności w celu wygenerowania obiektu COM z Visual Basic. W przypadku klas oznaczonych za pomocą `COMClassAttribute` kompilator wykonuje wiele z tych kroków automatycznie.

### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute

Użyj `HideModuleNameAttribute`, aby zezwolić na dostęp do członków modułu przy użyciu tylko kwalifikacji wymaganych dla modułu.

### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute

Użyj `VBFixedStringAttribute`, aby wymusić Visual Basic utworzyć ciąg o stałej długości. Ciągi są domyślnie o zmiennej długości, a ten atrybut jest przydatny podczas przechowywania ciągów do plików. Poniższy kod ilustruje:

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute

Użyj `VBFixedArrayAttribute`, aby zadeklarować tablice, których rozmiar jest ustalony. Podobnie jak Visual Basic ciągi, domyślnie tablice są o zmiennej długości. Ten atrybut jest przydatny podczas serializacji lub zapisywania danych w plikach.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
