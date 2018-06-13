---
title: Atrybuty wspólne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 5a91b0aa48a22db4ea7fb56a9c632ff0cb44dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644163"
---
# <a name="common-attributes-visual-basic"></a>Atrybuty wspólne (Visual Basic)
W tym temacie opisano atrybuty, które są najczęściej używane w programach Visual Basic.  
  
-   [Atrybuty globalne](#Global)  
  
-   [Atrybut przestarzałe](#Obsolete)  
  
-   [Atrybut Conditional](#Conditional)  
  
-   [Caller — atrybuty informacji](#CallerInfo)  
  
-   [Atrybuty Visual Basic](#VB)  
  
##  <a name="Global"></a> Atrybuty globalne  
 Większość atrybutów są stosowane do określonego języka elementów, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzanie informacji o wersji w zestawie, jak to:  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 Atrybuty globalne pojawiają się w kodzie źródłowym po jednej najwyższego poziomu `Imports` instrukcje i przed wszelkimi deklaracjami typu, modułu lub przestrzeni nazw. Atrybutami globalnymi może występować w wielu plikach źródłowych, ale muszą być skompilowane pliki w przebiegu kompilacji pojedynczej. W projektach Visual Basic atrybutami globalnymi zazwyczaj są umieszczane w pliku AssemblyInfo.vb (plik jest tworzona automatycznie podczas tworzenia projektu w programie Visual Studio).  
  
 Atrybuty zestawu wartości, które zawierają informacje o zestawie. Ich można podzielić na następujące kategorie:  
  
-   Atrybuty tożsamości zestawu  
  
-   Atrybuty informacyjny  
  
-   Atrybutów manifestu zestawu  
  
### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty (przy użyciu silnej nazwy, jeśli ma to zastosowanie) określić tożsamości zestawu: nazwa, wersja i kultury. Te atrybuty tworzą Pełna nazwa zestawu i są wymagane w przypadku odwołania w kodzie. Można ustawić wersja zestawu i kultury przy użyciu atrybutów. Jednak wartość nazwy jest ustawiony przez kompilator Visual Studio IDE w [informacji o zestawie — okno dialogowe](/visualstudio/ide/reference/assembly-information-dialog-box), lub Assembly Linker (Al.exe) podczas tworzenia zestawu oparty na pliku, który zawiera manifest zestawu. <xref:System.Reflection.AssemblyFlagsAttribute> Atrybut określa, czy wiele kopii zestawu mogą współistnieć.  
  
 W poniższej tabeli przedstawiono atrybuty tożsamości.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|Opis tożsamości zestawu.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa, które kultury obsługuje zestawu.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie side-by-side na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|  
  
### <a name="informational-attributes"></a>Atrybuty informacyjny  
 Atrybuty informacyjną umożliwia zapewniają dodatkowe firmy lub informacji o produkcie dla zestawu. W poniższej tabeli przedstawiono atrybuty informacyjną zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Definiuje atrybut niestandardowy, który określa nazwę produktu dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Określa niestandardowy atrybut, który określa znak towarowy dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Określa niestandardowy atrybut, który określa wersję informacyjny dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definiuje atrybut niestandardowy, który określa nazwę firmy dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definiuje atrybut niestandardowy, który określa copyright dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilator, aby używał odpowiedniego numeru wersji dla zasobu wersji pliku Win32.|  
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodne z typowych specyfikacji języka (CLS).|  
  
### <a name="assembly-manifest-attributes"></a>Atrybutów manifestu zestawu  
 Atrybutów manifestu zestawu można użyć, aby podać informacje w manifeście zestawu. W tym tytuł, opis, domyślny alias i konfiguracji. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Określa niestandardowy atrybut, który określa tytuł zestawu dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definiuje atrybut niestandardowy, który określa opis zestawu dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Określa niestandardowy atrybut, który określa konfigurację zestawu (na przykład detalicznych lub debugowanych) dla manifest zestawu.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje alias domyślne przyjazną dla manifest zestawu|  
  
##  <a name="Obsolete"></a> Atrybut przestarzałe  
 `Obsolete` Atrybut oznacza jednostki programu, co nie jest zalecane używanie. Każdym użyciu jednostki oznaczony jako przestarzały później spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu. Na przykład:  
  
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
  
 W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i do metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu stosowane do `B.OldMethod` ma ustawioną wartość `true`, ta metoda spowoduje błąd kompilatora, należy za pomocą klasy `A` będą tylko produktu ostrzeżenie. Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.  
  
 Dostarczony jako pierwszy argument do konstruktora atrybutu ciąg będą wyświetlane jako część ostrzeżenia lub błędu. Na przykład przypadku użycia jej wraz z definicjami poprzedniej następujący kod generuje dwa ostrzeżenia i jeden błąd:  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołania do klasy, a drugi dla konstruktora klasy.  
  
 `Obsolete` Atrybut może być używany bez argumentów, ale łącznie z wyjaśnieniem przyczyny element jest przestarzały i co należy użyć zamiast tego zaleca się.  
  
 `Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do dowolnej jednostki, który umożliwia atrybutów. `Obsolete` alias jest <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a> Atrybut Conditional  
 `Conditional` Atrybut powoduje, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego. `Conditional` Atrybutu jest aliasem <xref:System.Diagnostics.ConditionalAttribute>, można zastosować do metody lub atrybut klasy.  
  
 W tym przykładzie `Conditional` jest zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:  
  
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
  
 Jeśli `TRACE_ON` nie zdefiniowano identyfikatora, będą wyświetlane nie dane śledzenia.  
  
 `Conditional` Atrybutu jest często używane z `DEBUG` identyfikator do włączenia śledzenia i funkcje rejestrowania debugowania kompilacji, lecz nie w wersji kompilacji, podobnie do następującej:  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 Po wywołaniu metody oznaczone jako warunkowego obecności lub braku określony symbol przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięcia. Jeśli symbol jest zdefiniowany, wywołanie jest dołączony; w przeciwnym razie połączenie zostanie pominięty. Przy użyciu `Conditional` czyszczenia, jest bardziej elegancki i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloków w następujący sposób:  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 Metody warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Przy użyciu wielu identyfikatorów  
 Jeśli metoda ma wiele `Conditional` atrybuty, wywołanie do metody wchodzi Jeśli zdefiniowano co najmniej jeden z symboli warunkowego (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR). W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 Aby osiągnąć efekt logicznie łączenia symbole przy użyciu operatora AND, można zdefiniować serial metoda warunkowa. Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Przy użyciu warunkowego z klas atrybutów  
 `Conditional` Atrybut można stosować do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` tylko spowoduje dodanie informacji metadanych czy DEBUG jest zdefiniowane.  
  
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
  
##  <a name="CallerInfo"></a> Caller — atrybuty informacji  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Możesz uzyskać ścieżka pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o wywołującym — członek, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy parametr opcjonalny określenie wartości domyślnej. Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego ma zostać wywołana metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji o atrybutach wywołującego informacji, zobacz [informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
##  <a name="VB"></a> Atrybuty Visual Basic  
 W poniższej tabeli przedstawiono atrybuty, które są specyficzne dla języka Visual Basic.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|W kompilatorze wskazuje, czy obiekt modelu COM powinny zostać ujawnione klasy.|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|Zezwala członkom modułu można uzyskać dostęp przy użyciu kwalifikacji potrzebne dla modułu.|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|Określa rozmiar ciągu o stałej długości w strukturze do użycia z plikiem danych wejściowych i wyjściowych funkcji.|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|Określa rozmiar tablicy o ustalonym w strukturze do użycia z plikiem danych wejściowych i wyjściowych funkcji.|  
  
### <a name="comclassattribute"></a>COMClassAttribute  
 Użyj `COMClassAttribute` w celu uproszczenia procesu tworzenia składników COM z Visual Basic. Obiekty COM są znacznie różne zestawy .NET Framework i nie `COMClassAttribute`, należy wykonać kilka czynności, aby wygenerować obiektów COM z Visual Basic. Dla klasy oznaczonej `COMClassAttribute`, kompilator wykonuje wiele z tych kroków automatycznie.  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 Użyj `HideModuleNameAttribute` aby umożliwić członkom modułu można uzyskać dostęp za pomocą kwalifikacji potrzebne dla modułu.  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 Użyj `VBFixedStringAttribute` wymusić Visual Basic, aby utworzyć ciąg o stałej długości. Ciągi są o zmiennej długości domyślnie, a ten atrybut jest przydatne, gdy przechowywanie ciągów w plikach. Poniższy kod ilustruje to:  
  
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
 Użyj `VBFixedArrayAttribute` można deklarować tablic, które stałym rozmiarze. Podobnie jak ciągi Visual Basic tablic są o zmiennej długości domyślnie. Ten atrybut jest przydatne w przypadku serializacji lub zapisywanie danych w plikach.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Atrybuty](../../../../standard/attributes/index.md)  
 [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
