---
title: "Atrybuty wspólne (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e0a8912aa60e4c2918bb812963d83fae8d529f1
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="common-attributes-c"></a>Atrybuty wspólne (C#)
W tym temacie opisano atrybuty, które są najczęściej używane w programach języka C#.  
  
-   [Atrybuty globalne](#Global)  
  
-   [Atrybut przestarzałe](#Obsolete)  
  
-   [Atrybut Conditional](#Conditional)  
  
-   [Caller — atrybuty informacji](#CallerInfo)  
  
##  <a name="Global"></a>Atrybuty globalne  
 Większość atrybutów są stosowane do określonego języka elementów, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — odnoszą się do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzanie informacji o wersji w zestawie, jak to:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Atrybuty globalne pojawiają się w kodzie źródłowym po jednej najwyższego poziomu `using` dyrektywy i przed wszelkimi deklaracjami typu, modułu lub przestrzeni nazw. Atrybutami globalnymi może występować w wielu plikach źródłowych, ale muszą być skompilowane pliki w przebiegu kompilacji pojedynczej. W języku C# projektów atrybutami globalnymi są umieszczane w pliku AssemblyInfo.cs.  
  
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
  
##  <a name="Obsolete"></a>Atrybut przestarzałe  
 `Obsolete` Atrybut oznacza jednostki programu, co nie jest zalecane używanie. Każdym użyciu jednostki oznaczony jako przestarzały później spowoduje wygenerowanie ostrzeżenia lub błędu, w zależności od sposobu skonfigurowania atrybutu. Na przykład:  
  
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
  
 W tym przykładzie `Obsolete` atrybut jest stosowany do klasy `A` i do metody `B.OldMethod`. Ponieważ drugi argument konstruktora atrybutu stosowane do `B.OldMethod` ma ustawioną wartość `true`, ta metoda spowoduje błąd kompilatora, należy za pomocą klasy `A` będą tylko produktu ostrzeżenie. Wywoływanie `B.NewMethod`, jednak generuje nie ostrzeżenia lub błędu.  
  
 Dostarczony jako pierwszy argument do konstruktora atrybutu ciąg będą wyświetlane jako część ostrzeżenia lub błędu. Na przykład przypadku użycia jej wraz z definicjami poprzedniej następujący kod generuje dwa ostrzeżenia i jeden błąd:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Dwa ostrzeżenia dla klasy `A` są generowane: jeden dla deklaracji odwołania do klasy, a drugi dla konstruktora klasy.  
  
 `Obsolete` Atrybut może być używany bez argumentów, ale łącznie z wyjaśnieniem przyczyny element jest przestarzały i co należy użyć zamiast tego zaleca się.  
  
 `Obsolete` Atrybut jest atrybutem jednorazowego użytku i mogą być stosowane do dowolnej jednostki, który umożliwia atrybutów. `Obsolete`alias jest <xref:System.ObsoleteAttribute>.  
  
##  <a name="Conditional"></a>Atrybut Conditional  
 `Conditional` Atrybut powoduje, że wykonanie metody są zależne od identyfikatora przetwarzania wstępnego. `Conditional` Atrybutu jest aliasem <xref:System.Diagnostics.ConditionalAttribute>, można zastosować do metody lub atrybut klasy.  
  
 W tym przykładzie `Conditional` jest zastosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych programów:  
  
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
  
 Jeśli `TRACE_ON` nie zdefiniowano identyfikatora, będą wyświetlane nie dane śledzenia.  
  
 `Conditional` Atrybutu jest często używane z `DEBUG` identyfikator do włączenia śledzenia i funkcje rejestrowania debugowania kompilacji, lecz nie w wersji kompilacji, podobnie do następującej:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Po wywołaniu metody oznaczone jako warunkowego obecności lub braku określony symbol przetwarzania wstępnego Określa, czy wywołanie jest włączone, czy pominięcia. Jeśli symbol jest zdefiniowany, wywołanie jest dołączony; w przeciwnym razie połączenie zostanie pominięty. Przy użyciu `Conditional` czyszczenia, jest bardziej elegancki i mniej podatne na błędy zamiast otaczającej metody wewnątrz `#if…#endif` bloków w następujący sposób:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Metody warunkowego musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Przy użyciu wielu identyfikatorów  
 Jeśli metoda ma wiele `Conditional` atrybuty, wywołanie do metody wchodzi Jeśli zdefiniowano co najmniej jeden z symboli warunkowego (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR). W tym przykładzie obecności albo `A` lub `B` spowoduje wywołanie metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Aby osiągnąć efekt logicznie łączenia symbole przy użyciu operatora AND, można zdefiniować serial metoda warunkowa. Na przykład, druga metoda poniżej będą wykonywane tylko wtedy, gdy oba `A` i `B` są zdefiniowane:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Przy użyciu warunkowego z klas atrybutów  
 `Conditional` Atrybut można stosować do definicji klasy atrybutu. W tym przykładzie atrybut niestandardowy `Documentation` tylko spowoduje dodanie informacji metadanych czy DEBUG jest zdefiniowane.  
  
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
  
##  <a name="CallerInfo"></a>Caller — atrybuty informacji  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Możesz uzyskać ścieżka pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o wywołującym — członek, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy parametr opcjonalny określenie wartości domyślnej. Poniższa tabela zawiera listę atrybutów wywołującego informacje, które są zdefiniowane w <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego ma zostać wywołana metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji o atrybutach wywołującego informacji, zobacz [informacje o wywołującym (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Atrybuty](../../../../../docs/standard/attributes/index.md)  
 [Odbicie (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
