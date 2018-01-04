---
title: "Atrybuty — Przegląd (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b78eb3e5ac52ec89e810fde682249c689ba304a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-overview-visual-basic"></a>Atrybuty — Przegląd (Visual Basic)
Atrybuty udostępnia zaawansowane metody kojarzenia metadanych lub deklaratywne informacji z kodu (zestawy, typy metod, właściwości i tak dalej). Po atrybutu jest skojarzony z jednostką program, ten atrybut można tworzyć zapytania w czasie wykonywania przy użyciu techniki o nazwie *odbicia*. Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atrybuty mieć następujące właściwości:  
  
-   Atrybuty dodawać metadane do programu. *Metadane* znajdują się informacje o typy zdefiniowane w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych, które opisują typy i elementy członkowskie typu zdefiniowany w zestawie. Można dodawać atrybuty niestandardowe, aby określić dodatkowe informacje, które jest wymagane. Aby uzyskać więcej informacji zobacz, [tworzenie niestandardowe atrybuty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Co najmniej jeden atrybut można stosować do całego zestawy, moduły lub mniejsze elementy programu, takich jak klasy i właściwości.  
  
-   Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.  
  
-   Program można sprawdzić jego własnej ani metadanych w programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Przy użyciu atrybutów  
 Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut mogą ograniczać typów deklaracje, na których jest ona prawidłowa. W języku Visual Basic atrybutu jest ujęta w nawiasy (\< >). Musi znajdować się bezpośrednio przed elementem, do którego jest stosowana, w tym samym wierszu.  
  
 W tym przykładzie <xref:System.SerializableAttribute> atrybut służy do stosowania określonej właściwości do klasy:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowany w następujący sposób:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 Więcej niż jeden atrybut można umieścić w deklaracji:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Niektóre atrybuty można określić więcej niż raz dla danej jednostki. Na przykład multiuse atrybutu <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Według Konwencji wszystkich nazw atrybutów kończyć się wyrazem "Atrybutu", aby odróżnić je od innych elementów w programie .NET Framework. Nie trzeba jednak określić sufiks atrybutu przy użyciu atrybutów w kodzie. Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w programie .NET Framework.  
  
### <a name="attribute-parameters"></a>Parametry atrybutów  
 Wiele atrybutów ma parametry, które mogą być pozycyjnych, bez nazwy lub nazwane. Parametry pozycyjne musi być podana w odpowiedniej kolejności i nie może zostać pominięta; nazwane parametry są opcjonalne i może zostać określony w dowolnej kolejności. Parametry pozycyjne są określony jako pierwszy. Na przykład te trzy atrybuty są równoważne:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 Pierwszy parametr Nazwa biblioteki DLL jest pozycyjnych i zawsze zostanie osiągnięty jako pierwszy; inne o nazwie. W takim przypadku nazwanych parametrów domyślna wartość to false, więc można pominąć. Zajrzyj do dokumentacji poszczególne atrybuty, aby uzyskać informacje dotyczące domyślne wartości parametrów.  
  
### <a name="attribute-targets"></a>Docelowe atrybuty  
 *Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut. Na przykład atrybut mogą stosować do klasy, konkretnej metody lub całego zestawu. Domyślnie atrybut dotyczy poprzedza element. Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody, lub jej parametr albo jego wartości zwracanej.  
  
 Aby jawnie określić obiekt docelowy atrybutu, należy użyć następującej składni:  
  
```vb  
<target : attribute-list>  
```  
  
 Lista możliwości `target` w poniższej tabeli przedstawiono wartości.  
  
|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|  
|------------------|----------------|  
|`assembly`|Całego zestawu|  
|`module`|Bieżący modułu zestawu (który jest inny niż moduł Visual Basic)|  
  
 Poniższy przykład pokazuje, jak można zastosować atrybutów do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [takie same atrybuty wspólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Najczęstsze zastosowania dla atrybutów  
 Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:  
  
-   Oznaczanie za pomocą metody `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Zawierająca opis sposobu zorganizowania parametrów metody podczas współpracy z kodu macierzystego. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Opisujących właściwości modelu COM dla klas, metod i interfejsów.  
  
-   Wywoływanie niezarządzanych w kodzie za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.  
  
-   Opisujące używanemu zestawowi pod względem tytułu, wersji, opis lub znakiem towarowym.  
  
-   Opisujące członków klasy do serializacji trwałości.  
  
-   Opisujących sposób mapowania między elementami członkowskimi klas i węzłów XML do serializacji XML.  
  
-   Opisujących wymagania dotyczące zabezpieczeń dla metod.  
  
-   Określanie właściwości używanych do wymuszania zabezpieczeń.  
  
-   Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), kod jest łatwy do debugowania.  
  
-   Uzyskiwanie informacji o elemencie wywołującym metodę.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Porady: tworzenie złożenia C/C++ za pomocą atrybutów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Atrybuty wspólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)  
 [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Atrybuty](../../../../standard/attributes/index.md)
