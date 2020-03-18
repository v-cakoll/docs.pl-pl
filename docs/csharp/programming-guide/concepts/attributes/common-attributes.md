---
title: Typowe atrybuty (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399757"
---
# <a name="common-attributes-c"></a>Typowe atrybuty (C#)
W tym temacie opisano atrybuty, które są najczęściej używane w programach Języka C#.  
  
- [Atrybuty globalne](#Global)  
  
- [Przestarzały atrybut](#Obsolete)  
  
- [Atrybut warunkowy](#Conditional)  
  
- [Atrybuty informacji o obiekcie wywołującym](#CallerInfo)  
  
## <a name="Global"></a>Atrybuty globalne  
 Większość atrybutów są stosowane do określonych elementów języka, takich jak klasy lub metody; Jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji w zestawie, w tym sposób:  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 Atrybuty globalne są wyświetlane w kodzie `using` źródłowym po dowolnych dyrektywach najwyższego poziomu i przed dowolnym typem, modułem lub deklaracjami obszaru nazw. Atrybuty globalne mogą być wyświetlane w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji. W projektach języka C# atrybuty globalne są umieszczane w pliku AssemblyInfo.cs.  
  
 Atrybuty zestawu są wartościami, które dostarczają informacji o zestawie. Należą one do następujących kategorii:  
  
- Atrybuty tożsamości zestawu  
  
- Atrybuty informacyjne  
  
- Atrybuty manifestu zestawu  
  
### <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty (o silnej nazwie, jeśli dotyczy) określają tożsamość zestawu: nazwa, wersja i kultura. Atrybuty te tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do niego w kodzie. Można ustawić wersję zestawu i kultury przy użyciu atrybutów. Jednak wartość name jest ustawiana przez kompilator, IDE programu Visual Studio w [oknie dialogowym Informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator aplikacyjny zestawu (Al.exe) po utworzeniu zestawu na podstawie pliku zawierającego manifest zestawu. Atrybut <xref:System.Reflection.AssemblyFlagsAttribute> określa, czy wiele kopii zestawu może współistnieć.  
  
 W poniższej tabeli przedstawiono atrybuty tożsamości.  
  
|Atrybut|Przeznaczenie|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|W pełni opisuje tożsamość zestawu.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję zestawu.|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa, która kultura obsługuje zestaw.|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie obok siebie na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|  
  
### <a name="informational-attributes"></a>Atrybuty informacyjne  
 Atrybutów informacyjnych można użyć do podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli przedstawiono atrybuty informacyjne <xref:System.Reflection?displayProperty=nameWithType> zdefiniowane w obszarze nazw.  
  
|Atrybut|Przeznaczenie|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|Definiuje atrybut niestandardowy, który określa nazwę produktu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Definiuje atrybut niestandardowy, który określa znak towarowy dla manifestu złożenia.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Definiuje atrybut niestandardowy, który określa wersję informacyjną dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Definiuje atrybut niestandardowy, który określa nazwę firmy dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definiuje atrybut niestandardowy, który określa prawa autorskie do manifestu zestawu.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Instruuje kompilator, aby użył określonego numeru wersji dla zasobu wersji pliku Win32.|  
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodny ze specyfikacją języka wspólnego (CLS).|  
  
### <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu  
 Atrybuty manifestu zestawu można użyć do dostarczenia informacji w manifeście zestawu. Obejmuje to tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli przedstawiono atrybuty manifestu zestawu zdefiniowane w obszarze <xref:System.Reflection?displayProperty=nameWithType> nazw.  
  
|Atrybut|Przeznaczenie|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Definiuje atrybut niestandardowy, który określa tytuł zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Definiuje atrybut niestandardowy, który określa opis zestawu dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Definiuje atrybut niestandardowy, który określa konfigurację zestawu (na przykład sprzedaży detalicznej lub debugowania) dla manifestu zestawu.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje przyjazny alias domyślny dla manifestu zestawu|  
  
## <a name="Obsolete"></a>Przestarzały atrybut  
 Atrybut `Obsolete` oznacza jednostkę programu jako jednostkę, która nie jest już zalecana do użycia. Każde użycie jednostki oznaczone jako przestarzałe spowoduje następnie wygenerować ostrzeżenie lub błąd, w zależności od sposobu skonfigurowania atrybutu. Przykład:  
  
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
  
 W tym `Obsolete` przykładzie atrybut jest `A` stosowany do `B.OldMethod`klasy i metody . Ponieważ drugi argument konstruktora atrybutu stosowane do `B.OldMethod` jest ustawiona na `true`, ta metoda `A` spowoduje błąd kompilatora, podczas gdy przy użyciu klasy będzie po prostu utworzyć ostrzeżenie. Wywołanie `B.NewMethod`, jednak nie generuje żadnego ostrzeżenia lub błędu.  
  
 Ciąg podany jako pierwszy argument konstruktora atrybutu zostanie wyświetlony jako część ostrzeżenia lub błędu. Na przykład, gdy używasz go z poprzednimi definicjami, poniższy kod generuje dwa ostrzeżenia i jeden błąd:  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 Generowane są dwa `A` ostrzeżenia dla klasy: jeden dla deklaracji odwołania do klasy i jeden dla konstruktora klasy.  
  
 Atrybut `Obsolete` może być używany bez argumentów, ale w tym wyjaśnienie, dlaczego element jest przestarzały i co zamiast tego jest zalecane.  
  
 Atrybut `Obsolete` jest atrybutem jednorazowego użytku i może być stosowany do dowolnej encji, która zezwala na atrybuty. `Obsolete`jest aliasem <xref:System.ObsoleteAttribute>dla .  
  
## <a name="Conditional"></a>Atrybut warunkowy  
 Atrybut `Conditional` sprawia, że wykonanie metody zależy od identyfikatora wstępnego przetwarzania. Atrybut `Conditional` jest aliasem <xref:System.Diagnostics.ConditionalAttribute>dla i może być stosowany do metody lub klasy atrybutu.  
  
 W tym `Conditional` przykładzie jest stosowany do metody, aby włączyć lub wyłączyć wyświetlanie informacji diagnostycznych specyficznych dla programu:  
  
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
  
 Jeśli `TRACE_ON` identyfikator nie jest zdefiniowany, nie zostaną wyświetlone żadne dane wyjściowe śledzenia.  
  
 Atrybut `Conditional` jest często używany `DEBUG` z identyfikatorem, aby włączyć śledzenie i rejestrowanie funkcji dla kompilacji debugowania, ale nie w kompilacjach wersji, w tym sposób:  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 Gdy wywoływana jest metoda oznaczona jako warunkowa, obecność lub brak określonego symbolu przetwarzania wstępnego określa, czy wywołanie jest uwzględnione, czy pominięte. Jeśli symbol jest zdefiniowany, połączenie jest uwzględniane; w przeciwnym razie wywołanie zostanie pominięte. Korzystanie `Conditional` jest czystszą, bardziej elegancką i mniej `#if…#endif` podatną na błędy alternatywą dla załączania metod wewnątrz bloków, w tym stylu:  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 Metoda warunkowa musi być metodą w deklaracji klasy lub struktury i nie może mieć wartości zwracanej.  
  
### <a name="using-multiple-identifiers"></a>Używanie wielu identyfikatorów  
 Jeśli metoda ma `Conditional` wiele atrybutów, wywołanie metody jest uwzględniane, jeśli zdefiniowano co najmniej jeden z symboli warunkowych (innymi słowy, symbole są logicznie połączone ze sobą za pomocą operatora OR). W tym przykładzie obecność `A` albo `B` spowoduje wywołanie metody:  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 Aby osiągnąć efekt logicznego łączenia symboli za pomocą operatora AND, można zdefiniować szeregowe metody warunkowe. Na przykład druga metoda poniżej zostanie `A` wykonana `B` tylko wtedy, gdy oba i są zdefiniowane:  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a>Używanie warunkowego z klasami atrybutów  
 Atrybut `Conditional` można również zastosować do definicji klasy atrybutu. W tym przykładzie atrybut `Documentation` niestandardowy doda informacje do metadanych tylko wtedy, gdy zdefiniowano DEBUG.  
  
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
  
## <a name="CallerInfo"></a>Atrybuty informacji o obiekcie wywołującym  
 Przy użyciu atrybutów informacji o obiekcie wywołującym można uzyskać informacje o obiekcie wywołującym metodę. Ścieżkę pliku kodu źródłowego, numer wiersza w kodzie źródłowym i nazwę elementu członkowskiego obiektu wywołującego.  
  
 Aby uzyskać informacje o obiekcie wywołującym element członkowski, należy użyć atrybutów, które są stosowane do parametrów opcjonalnych. Każdy parametr opcjonalny określa wartość domyślną. W poniższej tabeli wymieniono atrybuty Informacje <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> o obiekcie wywołującym zdefiniowane w obszarze nazw:  
  
|Atrybut|Opis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Pełna ścieżka pliku źródłowego zawierającego obiekt wywołujący. Jest to ścieżka w czasie kompilacji.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numer wiersza w pliku źródłowym, z którego wywoływana jest metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nazwa metody lub nazwa właściwości obiektu wywołującego. Aby uzyskać więcej informacji, zobacz [Informacje o obiekcie wywołującym (C#)](../caller-information.md).|`String`|  
  
 Aby uzyskać więcej informacji o atrybutach informacje o obiekcie wywołującym, zobacz [Informacje o obiekcie wywołującym (C#)](../caller-information.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania języka C#](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (C#)](../reflection.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](./accessing-attributes-by-using-reflection.md)
