---
title: Atrybuty wspólne (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 4a1dd6200f7eb9e69caefe62d9e9defd90856ce1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558595"
---
# <a name="common-attributes-c"></a>Atrybuty wspólne (C#)
W tym temacie opisano atrybuty, które są najczęściej używane w programach języka C#.  
  
-   [Atrybuty globalne](#Global)  
  
-   [Atrybut przestarzałe](#Obsolete)  
  
-   [Atrybut Conditional](#Conditional)  
  
-   [Caller — atrybuty informacji](#CallerInfo)  
  
##  <a name="Global"></a> Atrybuty globalne  
 Większość atrybuty są stosowane do elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacje o wersji w zespół, takich jak to:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Atrybuty globalne są wyświetlane w kodzie źródłowym po każdym najwyższego poziomu `using` dyrektyw i przed deklaracjami dowolnego typu, modułu lub przestrzeni nazw. Atrybuty globalne mogą być wyświetlane w wielu plikach źródłowych, ale pliki muszą być skompilowane w pojedynczej kompilacji przebiegu. W projektach C# atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.  
  
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
  
##  <a name="Obsolete"></a> Atrybut przestarzałe  
 `Obsolete` Atrybut oznacza jednostka program jako taki, który nie jest już zalecany do użycia. Każde użycie jednostki oznaczony jako przestarzały później, spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu. Na przykład:  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` oraz metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu jest stosowane do `B.OldMethod` ustawiono `true`, ta metoda spowoduje błąd kompilatora, natomiast przy użyciu klasy `A` będzie po prostu wygenerować ostrzeżenie. Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.  
  
 Ciąg, podana jako pierwszy argument konstruktora atrybutu będą wyświetlane jako część ostrzeżenia lub błędu. Na przykład podczas korzystania z poprzednim definicje, poniższy kod generuje dwa ostrzeżenia i jeden błąd:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołań do klas i jeden dla konstruktora klasy.  
  
 `Obsolete` Atrybut może być używana bez argumentów, ale tym wyjaśnienie, dlaczego elementu jest przestarzały i nie zamiast tego użyć zalecanych.  
  
 `Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do każda jednostka, która umożliwia atrybutów. `Obsolete` jest aliasem <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a> Atrybut Conditional  
 `Conditional` Atrybutu sprawia, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego. `Conditional` Atrybut jest aliasem <xref:System.Diagnostics.ConditionalAttribute>i mogą być stosowane do metodę lub klasę atrybutów.  
  
 W tym przykładzie `Conditional` zostanie zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, będą wyświetlane żadne dane wyjściowe śledzenia.  
  
 `Conditional` Atrybutu jest często używana z `DEBUG` identyfikator, aby włączyć śledzenie i rejestrowanie funkcji, wydajność debugowania kompilacji, ale nie w wersji kompilacji, podobnie do następującego:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Gdy wywoływana jest metoda oznaczona jako warunkowe, obecności lub braku określonego symbolu przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięty. Jeśli zdefiniowano symbol wywołanie jest uwzględniany; w przeciwnym razie wywołanie zostanie pominięty. Za pomocą `Conditional` jest bardziej przejrzystą i bardziej eleganckim i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloki następująco:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Metoda warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Przy użyciu wielu identyfikatorów  
 Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie do metody jest dołączona, jeśli zdefiniowano co najmniej jeden z warunkowego symbole (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR). W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Aby osiągnąć ten efekt logicznie łączenia symbole za pomocą operatora AND, można zdefiniować serial metoda warunkowa. Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>Używanie warunkowego z klas atrybutów  
 `Conditional` Atrybut można stosować do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` tylko doda informacje metadanych Jeśli DEBUG jest zdefiniowane.  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <a name="CallerInfo"></a> Caller — atrybuty informacji  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Można uzyskać ścieżkę pliku kodu źródłowego, numer wiersza kodu źródłowego i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o wywołującym elementu członkowskiego, należy użyć atrybutów stosowanych do opcjonalnych parametrów. Każdy parametr opcjonalny określenie wartości domyślnej. W poniższej tabeli przedstawiono atrybuty informacji o obiekcie wywołującym, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, w którym metoda jest wywoływana.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości name obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji na temat atrybutów informacji o obiekcie wywołującym zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
- [Atrybuty](../../../../../docs/standard/attributes/index.md)
- [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
