---
title: Atrybuty wspólne
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 57ef8f103d64a51d896f46d2889d78ec99ff3223
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400722"
---
# <a name="common-attributes-visual-basic"></a>Atrybuty wspólne (Visual Basic)

W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.

- [Atrybuty globalne](#Global)

- [Przestarzały atrybut](#Obsolete)

- [Atrybut warunkowy](#Conditional)

- [Atrybuty informacji o wywołującym](#CallerInfo)

- [Atrybuty Visual Basic](#VB)

## <a name="global-attributes"></a><a name="Global"></a>Atrybuty globalne

Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, takich jak:

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

Atrybuty globalne pojawiają się w kodzie źródłowym po dowolnych instrukcjach najwyższego poziomu `Imports` i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw. Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji. W przypadku projektów Visual Basic atrybuty globalne są zwykle umieszczane w pliku AssemblyInfo. vb (plik jest tworzony automatycznie podczas tworzenia projektu w programie Visual Studio).

Atrybuty zestawu są wartościami, które zawierają informacje o zestawie. Należą do następujących kategorii:

- Atrybuty tożsamości zestawu

- Atrybuty informacyjne

- Atrybuty manifestu zestawu

### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu

Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie. Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów. Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu. Ten <xref:System.Reflection.AssemblyFlagsAttribute> atrybut określa, czy wiele kopii zestawu może współistnieć.

W poniższej tabeli przedstawiono atrybuty tożsamości.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|W pełni opisuje tożsamość zestawu.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa kulturę obsługiwaną przez zestaw.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|

### <a name="informational-attributes"></a>Atrybuty informacyjne

Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Definiuje niestandardowy atrybut, który określa nazwę produktu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definiuje niestandardowy atrybut, który określa znak towarowy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definiuje niestandardowy atrybut, który określa wersję informacyjną dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definiuje niestandardowy atrybut, który określa nazwę firmy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definiuje niestandardowy atrybut, który określa prawo autorskie dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilator, aby używał określonego numeru wersji dla zasobu wersji plików Win32.|
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).|

### <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu

Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu. Obejmuje to tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje przyjazny alias domyślny dla manifestu zestawu|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a>Przestarzały atrybut

Ten `Obsolete` atrybut oznacza jednostkę programu, która nie jest już zalecana do użycia. Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu. Przykład:

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

W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i metody `B.OldMethod` . Ponieważ drugi argument konstruktora atrybutu stosowany do `B.OldMethod` jest ustawiony na `true` , ta metoda spowoduje błąd kompilatora, podczas gdy użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia. Jednak wywoływanie `B.NewMethod` nie powoduje żadnych ostrzeżeń ani błędów.

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

Generowane są dwa ostrzeżenia dla klasy `A` : jeden dla deklaracji klasy Reference i jeden dla konstruktora klasy.

Ten `Obsolete` atrybut może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.

Ten `Obsolete` atrybut jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty. `Obsolete`jest aliasem dla <xref:System.ObsoleteAttribute> .

## <a name="conditional-attribute"></a><a name="Conditional"></a>Atrybut warunkowy

Ten `Conditional` atrybut wykonuje metodę zależną od identyfikatora przetwarzania wstępnego. `Conditional`Atrybut jest alias dla <xref:System.Diagnostics.ConditionalAttribute> i może być zastosowany do metody lub klasy atrybutu.

W tym przykładzie `Conditional` stosuje się do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:

```vb
#Const TRACE_ON = True
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

Jeśli `TRACE_ON` Identyfikator nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.

Ten `Conditional` atrybut jest często używany z `DEBUG` identyfikatorem, aby włączyć funkcje śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydania, takich jak:

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte. Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte. Korzystanie z programu `Conditional` to przejrzysty, bardziej elegancki i mniej podatny na błędy alternatywa dla otaczających metod w `#if…#endif` blokach, takich jak:

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.

### <a name="using-multiple-identifiers"></a>Używanie wielu identyfikatorów

Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR). W tym przykładzie, obecność albo `A` `B` spowoduje wywołanie metody:

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe. Na przykład druga metoda zostanie wykonana tylko wtedy, gdy obie `A` i `B` są zdefiniowane:

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

Ten `Conditional` atrybut może być również stosowany do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.

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

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a>Atrybuty informacji o wywołującym

Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.

Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy opcjonalny parametr określa wartość domyślną. W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:

|Atrybut|Opis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub nazwa właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [Informacje o wywołującym (Visual Basic)](../caller-information.md).|`String`|

Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującym (Visual Basic)](../caller-information.md).

## <a name="visual-basic-attributes"></a><a name="VB"></a>Atrybuty Visual Basic

W poniższej tabeli wymieniono atrybuty, które są specyficzne dla Visual Basic.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|Wskazuje kompilatorowi, że klasa powinna być udostępniana jako obiekt COM.|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Zezwala na dostęp do elementów członkowskich modułu wyłącznie przy użyciu kwalifikacji wymaganych dla modułu.|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Określa rozmiar ciągu o stałej długości w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Określa rozmiar stałej tablicy w strukturze do użycia z funkcjami wejściowymi i wyjściowymi plików.|

### <a name="comclassattribute"></a>COMClassAttribute

Użyj `COMClassAttribute` , aby uprościć proces tworzenia składników modelu COM z Visual Basic. Obiekty COM różnią się znacznie od zestawów .NET Framework i nie należy `COMClassAttribute` wykonać kilku kroków w celu wygenerowania obiektu com z Visual Basic. W przypadku klas oznaczonych za pomocą `COMClassAttribute` kompilator wykonuje wiele czynności automatycznie.

### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute

Służy `HideModuleNameAttribute` do zezwalania na dostęp do elementów członkowskich modułu przy użyciu tylko kwalifikacji wymaganych przez moduł.

### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute

Użyj `VBFixedStringAttribute` , aby wymusić Visual Basic utworzyć ciąg o stałej długości. Ciągi są domyślnie o zmiennej długości, a ten atrybut jest przydatny podczas przechowywania ciągów do plików. Poniższy kod ilustruje:

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

Służy `VBFixedArrayAttribute` do deklarowania tablic, które mają stały rozmiar. Podobnie jak Visual Basic ciągi, domyślnie tablice są o zmiennej długości. Ten atrybut jest przydatny podczas serializacji lub zapisywania danych w plikach.

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w Visual Basic](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../reflection.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md)
