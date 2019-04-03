---
title: Atrybuty wspólne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: e001c9a637d2e5e34e77158704e4ad81d6973a50
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834549"
---
# <a name="common-attributes-visual-basic"></a>Atrybuty wspólne (Visual Basic)
W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.  
  
-   [Atrybuty globalne](#Global)  
  
-   [Atrybut przestarzałe](#Obsolete)  
  
-   [Atrybut Conditional](#Conditional)  
  
-   [Caller — atrybuty informacji](#CallerInfo)  
  
-   [Atrybuty Visual Basic](#VB)  
  
## <a name="Global"></a> Atrybuty globalne  
 Większość atrybuty są stosowane do elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacje o wersji w zespół, takich jak to:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Atrybuty globalne są wyświetlane w kodzie źródłowym po każdym najwyższego poziomu `Imports` instrukcji i przed deklaracjami dowolnego typu, modułu lub przestrzeni nazw. Atrybuty globalne mogą być wyświetlane w wielu plikach źródłowych, ale pliki muszą być skompilowane w pojedynczej kompilacji przebiegu. W przypadku projektów Visual Basic atrybutami globalnymi zazwyczaj są umieszczane w pliku AssemblyInfo.vb (pliku jest tworzona automatycznie podczas tworzenia projektu w programie Visual Studio).  
  
 Atrybuty zestawu są wartości, które dostarczają informacje o zestawie. Można je podzielić na następujące kategorie:  
  
-   Atrybuty tożsamości zestawu  
  
-   Atrybuty informacyjne  
  
-   Atrybuty manifestu zestawu  
  
### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty (silną nazwą, jeśli ma to zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane, gdy można się odwoływać w kodzie. Można ustawić wersję i kulturę przy użyciu atrybutów zestawu. Jednak nazwa ma wartość przez kompilator programu Visual Studio IDE w [informacje o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box), lub Assembly Linker (Al.exe), po utworzeniu zestawu w oparciu o plik, który zawiera manifest zestawu. <xref:System.Reflection.AssemblyFlagsAttribute> Atrybut określa, czy wiele kopii zestawu mogą współistnieć.  
  
 W poniższej tabeli przedstawiono atrybuty tożsamości.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|W pełni opisuje tożsamości zestawu.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa, które kultury obsługuje zestawu.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie side-by-side na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|  
  
### <a name="informational-attributes"></a>Atrybuty informacyjne  
 Aby zapewnić dodatkowe firmy lub informacje o produkcie dla zestawu, można użyć atrybuty informacyjne. W poniższej tabeli przedstawiono atrybuty informacyjne, zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Określa niestandardowy atrybut, który określa nazwę produktu w manifeście zestawu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definiuje atrybutu niestandardowego, który określa znak towarowy manifestu zestawu.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Określa niestandardowy atrybut, który określa informacjami o wersji dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Określa atrybut niestandardowy, który określa nazwę firmy na potrzeby manifestu zestawu.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Określa niestandardowy atrybut, który określa prawa autorskiego manifestu zestawu.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilator, aby użyć numeru wersji określonej dla zasobu wersji pliku systemu Win32.|  
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodny z Common Language Specification (CLS).|  
  
### <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu  
 Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu. W tym tytuł, opis, domyślny alias i konfiguracji. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowanych w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Określa niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Określa niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład sprzedaży detalicznej lub debugowanie) w manifeście zestawu.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Określa przyjazną domyślny alias manifestu zestawu|  
  
## <a name="Obsolete"></a> Atrybut przestarzałe  
 `Obsolete` Atrybut oznacza jednostka program jako taki, który nie jest już zalecany do użycia. Każde użycie jednostki oznaczony jako przestarzały później, spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu. Na przykład:  
  
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
  
 W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` oraz metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu jest stosowane do `B.OldMethod` ustawiono `true`, ta metoda spowoduje błąd kompilatora, natomiast przy użyciu klasy `A` będzie po prostu wygenerować ostrzeżenie. Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.  
  
 Ciąg, podana jako pierwszy argument konstruktora atrybutu będą wyświetlane jako część ostrzeżenia lub błędu. Na przykład podczas korzystania z poprzednim definicje, poniższy kod generuje dwa ostrzeżenia i jeden błąd:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołań do klas i jeden dla konstruktora klasy.  
  
 `Obsolete` Atrybut może być używana bez argumentów, ale tym wyjaśnienie, dlaczego elementu jest przestarzały i nie zamiast tego użyć zalecanych.  
  
 `Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do każda jednostka, która umożliwia atrybutów. `Obsolete` jest aliasem <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a> Atrybut Conditional  
 `Conditional` Atrybutu sprawia, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego. `Conditional` Atrybut jest aliasem <xref:System.Diagnostics.ConditionalAttribute>i mogą być stosowane do metodę lub klasę atrybutów.  
  
 W tym przykładzie `Conditional` zostanie zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:  
  
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
  
 Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, będą wyświetlane żadne dane wyjściowe śledzenia.  
  
 `Conditional` Atrybutu jest często używana z `DEBUG` identyfikator, aby włączyć śledzenie i rejestrowanie funkcji, wydajność debugowania kompilacji, ale nie w wersji kompilacji, podobnie do następującego:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Gdy wywoływana jest metoda oznaczona jako warunkowe, obecności lub braku określonego symbolu przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięty. Jeśli zdefiniowano symbol wywołanie jest uwzględniany; w przeciwnym razie wywołanie zostanie pominięty. Za pomocą `Conditional` jest bardziej przejrzystą i bardziej eleganckim i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloki następująco:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Metoda warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Przy użyciu wielu identyfikatorów  
 Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie do metody jest dołączona, jeśli zdefiniowano co najmniej jeden z warunkowego symbole (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR). W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Aby osiągnąć ten efekt logicznie łączenia symbole za pomocą operatora AND, można zdefiniować serial metoda warunkowa. Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Używanie warunkowego z klas atrybutów  
 `Conditional` Atrybut można stosować do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` tylko doda informacje metadanych Jeśli DEBUG jest zdefiniowane.  
  
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
  
## <a name="CallerInfo"></a> Caller — atrybuty informacji  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o wywołującym elementu członkowskiego, należy użyć atrybutów stosowanych do opcjonalnych parametrów. Każdy parametr opcjonalny określenie wartości domyślnej. W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, w którym metoda jest wywoływana.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości name obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji na temat atrybutów informacji o obiekcie wywołującym zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
## <a name="VB"></a> Atrybuty Visual Basic  
 W poniższej tabeli przedstawiono atrybuty, które są specyficzne dla języka Visual Basic.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|W kompilatorze wskazuje, czy klasa powinna być udostępniana jako obiekt COM.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Zezwala członkom modułu, można uzyskać za pomocą tylko kwalifikacji, które są wymagane dla modułu.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Określa rozmiar ciągu o stałej długości w strukturze do użytku z plikiem danych wejściowych i wyjściowych funkcji.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Określa rozmiar tablicy stałych w strukturze do użytku z plikiem danych wejściowych i wyjściowych funkcji.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Użyj `COMClassAttribute` w celu uproszczenia procesu tworzenia składników modelu COM z Visual Basic. Obiekty COM różnią się znacznie od zestawów .NET Framework i bez `COMClassAttribute`, należy wykonać kilka kroków, aby wygenerować obiektów COM z Visual Basic. Dla klasy oznaczone atrybutem `COMClassAttribute`, kompilator wykonuje wiele z tych kroków automatycznie.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Użyj `HideModuleNameAttribute` aby umożliwić członkom modułu, można uzyskać dostęp za pomocą tylko kwalifikacji, które są wymagane dla modułu.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Użyj `VBFixedStringAttribute` wymusić Visual Basic, aby utworzyć ciąg znaków o stałej długości. Ciągi są o zmiennej długości, domyślnie, a ten atrybut jest przydatna w przypadku przechowywania ciągów do plików. Poniższy kod przedstawia to:  
  
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
 Użyj `VBFixedArrayAttribute` do deklarują tablice, które zostały rozwiązane w rozmiarze. Na przykład ciągi języka Visual Basic tablice są o zmiennej długości, domyślnie. Ten atrybut jest przydatna, gdy serializacji lub zapisywanie danych w plikach.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
