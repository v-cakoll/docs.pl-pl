---
title: Atrybuty wspólne (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595459"
---
# <a name="common-attributes-c"></a>Atrybuty wspólne (C#)
W tym temacie opisano atrybuty, które są najczęściej używane w C# programach.  
  
- [Atrybuty globalne](#Global)  
  
- [Przestarzały atrybut](#Obsolete)  
  
- [Atrybut warunkowy](#Conditional)  
  
- [Atrybuty informacji o wywołującym](#CallerInfo)  
  
## <a name="Global"></a>Atrybuty globalne  
 Większość atrybutów stosuje się do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, takich jak:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Atrybuty globalne pojawiają się w kodzie źródłowym po dowolnych `using` dyrektywach najwyższego poziomu i przed dowolnymi deklaracjami typu, modułu lub przestrzeni nazw. Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji. W C# projektach atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.  
  
 Atrybuty zestawu są wartościami, które zawierają informacje o zestawie. Należą do następujących kategorii:  
  
- Atrybuty tożsamości zestawu  
  
- Atrybuty informacyjne  
  
- Atrybuty manifestu zestawu  
  
### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty (o silnej nazwie, jeśli ma zastosowanie) określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie. Możesz ustawić wersję zestawu i kulturę przy użyciu atrybutów. Jednak wartość nazwy jest ustawiana przez kompilator, środowisko IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al. exe) podczas tworzenia zestawu, na podstawie pliku, który zawiera manifest zestawu. Ten <xref:System.Reflection.AssemblyFlagsAttribute> atrybut określa, czy wiele kopii zestawu może współistnieć.  
  
 W poniższej tabeli przedstawiono atrybuty tożsamości.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|W pełni opisuje tożsamość zestawu.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa kulturę obsługiwaną przez zestaw.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie równoczesne na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|  
  
### <a name="informational-attributes"></a>Atrybuty informacyjne  
 Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli przedstawiono atrybuty informacyjne zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
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
 Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu. Obejmuje to tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w <xref:System.Reflection?displayProperty=nameWithType> przestrzeni nazw.  
  
|Atrybut|Cel|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definiuje niestandardowy atrybut, który określa tytuł zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definiuje niestandardowy atrybut, który określa opis zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definiuje niestandardowy atrybut, który określa konfigurację zestawu (na przykład detaliczną lub Debug) dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje przyjazny alias domyślny dla manifestu zestawu|  
  
## <a name="Obsolete"></a>Przestarzały atrybut  
 Ten `Obsolete` atrybut oznacza jednostkę programu, która nie jest już zalecana do użycia. Każde użycie jednostki oznaczonej jako przestarzałe spowoduje wygenerowanie ostrzeżenia lub błędu w zależności od sposobu skonfigurowania atrybutu. Na przykład:  
  
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
  
 W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu stosowany do `B.OldMethod` jest ustawiony na `true`, ta metoda spowoduje błąd kompilatora, podczas gdy użycie klasy `A` spowoduje po prostu wygenerowanie ostrzeżenia. Jednak `B.NewMethod`wywoływanie nie powoduje żadnych ostrzeżeń ani błędów.  
  
 Ciąg dostarczony jako pierwszy argument konstruktora atrybutu będzie wyświetlany jako część ostrzeżenia lub błędu. Na przykład jeśli używasz go z poprzednimi definicjami, poniższy kod generuje dwie ostrzeżenia i jeden błąd:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Generowane są dwa ostrzeżenia `A` dla klasy: jeden dla deklaracji klasy Reference i jeden dla konstruktora klasy.  
  
 Ten `Obsolete` atrybut może być używany bez argumentów, ale wraz z wyjaśnieniem dlaczego element jest przestarzały i czego należy używać.  
  
 Ten `Obsolete` atrybut jest atrybutem jednokrotnego użycia i może być stosowany do każdej jednostki, która zezwala na atrybuty. `Obsolete`jest aliasem dla <xref:System.ObsoleteAttribute>.  
  
## <a name="Conditional"></a>Atrybut warunkowy  
 Ten `Conditional` atrybut wykonuje metodę zależną od identyfikatora przetwarzania wstępnego. Atrybut jest alias dla <xref:System.Diagnostics.ConditionalAttribute>i może być zastosowany do metody lub klasy atrybutu. `Conditional`  
  
 W tym przykładzie `Conditional` stosuje się do metody w celu włączenia lub wyłączenia wyświetlania informacji diagnostycznych specyficznych dla programu:  
  
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
  
 `TRACE_ON` Jeśli identyfikator nie jest zdefiniowany, nie będą wyświetlane dane wyjściowe śledzenia.  
  
 Ten `Conditional` atrybut jest często używany `DEBUG` z identyfikatorem, aby włączyć funkcje śledzenia i rejestrowania dla kompilacji debugowania, ale nie w kompilacjach wydania, takich jak:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest dołączone czy pominięte. Jeśli symbol jest zdefiniowany, wywołanie jest dołączone; w przeciwnym razie wywołanie zostanie pominięte. Korzystanie `Conditional` z programu to przejrzysty, bardziej elegancki i mniej podatny na błędy alternatywa dla otaczających `#if…#endif` metod w blokach, takich jak:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Używanie wielu identyfikatorów  
 Jeśli metoda ma wiele `Conditional` atrybutów, wywołanie metody jest uwzględnione, jeśli co najmniej jeden z symboli warunkowych jest zdefiniowany (innymi słowy, symbole są logicznie połączone ze sobą przy użyciu operatora OR). W tym przykładzie, obecność albo `A` `B` spowoduje wywołanie metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora i, można zdefiniować metody warunkowe szeregowe. Na przykład druga metoda zostanie wykonana tylko wtedy, gdy obie `A` i `B` są zdefiniowane:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Używanie warunkowe z klasami atrybutów  
 Ten `Conditional` atrybut może być również stosowany do definicji klasy atrybutu. W tym przykładzie atrybut `Documentation` niestandardowy będzie dodawać tylko informacje do metadanych w przypadku zdefiniowania debugowania.  
  
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
  
## <a name="CallerInfo"></a>Atrybuty informacji o wywołującym  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Możesz uzyskać ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o obiekcie wywołującym elementu członkowskiego, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy opcjonalny parametr określa wartość domyślną. W poniższej tabeli wymieniono atrybuty informacji o wywołującym, które są <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> zdefiniowane w przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub nazwa właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [Informacje oC#wywołującym ()](../caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji o atrybutach informacji o wywołującym, zobacz [Informacje o wywołującymC#()](../caller-information.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku C#](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [OdbicieC#()](../reflection.md)
- [Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()](./accessing-attributes-by-using-reflection.md)
