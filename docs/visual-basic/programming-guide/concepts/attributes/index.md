---
title: Omówienie atrybuty (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: 2ecc3fb0a3bf7365b6eec39e1c5086d99f2c5a19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642455"
---
# <a name="attributes-overview-visual-basic"></a>Omówienie atrybuty (Visual Basic)
Atrybuty zawierają zaawansowaną metodą kojarzenia metadanych lub informacji deklaratywne, przy użyciu kodu (zestawy, typy, metody, właściwości i tak dalej). Po atrybutu jest skojarzony z jednostką program, ten atrybut można wykonywać zapytania w czasie wykonywania za pomocą technikę o nazwie *odbicia*. Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atrybuty mają następujące właściwości:  
  
- Atrybuty dodawania metadanych do programu. *Metadane* obejmuje informacje dotyczące typów zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadane opisujące typy i elementy członkowskie typu zdefiniowane w zestawie. Możesz dodać atrybuty niestandardowe, aby określić dodatkowe informacje, która jest wymagana. Aby uzyskać więcej informacji znajduje się pozycja [tworzenia atrybuty niestandardowe (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
- Jeden lub więcej atrybutów mogą dotyczyć całego zestawów, modułów lub mniejszych elementów programów, takich jak klasy i właściwości.  
  
- Atrybuty można zaakceptować argumentów w taki sam sposób jak metody i właściwości.  
  
- Program można sprawdzić swój własny metadanych lub metadanych w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Przy użyciu atrybutów  
 Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy. W języku Visual Basic atrybut jest ujęty w nawiasy ostre (\< >). Musi znajdować się bezpośrednio przed elementem, do którego jest stosowana, w tym samym wierszu.  
  
 W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania szczególne właściwości do klasy:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana następująco:  
  
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
  
 Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki. Na przykład multiuse — atrybut <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  Zgodnie z Konwencją wszystkie nazwy atrybutu kończą się wyrazem "Atrybut", aby odróżnić je od innych elementów w .NET Framework. Nie musisz jednak określić sufiks atrybutu, korzystając z atrybutów w kodzie. Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w .NET Framework.  
  
### <a name="attribute-parameters"></a>Parametry atrybutów  
 Wiele atrybutów ma parametry, które mogą być pozycyjne, bez nazwy lub nazwane. Wszystkie parametry pozycyjne musi być określona w określonej kolejności i nie może zostać pominięta; Parametry nazwane są opcjonalne i może być określony w dowolnej kolejności. Parametry pozycyjne są określony jako pierwszy. Na przykład te trzy atrybuty są równoważne:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 Pierwszy parametr, nazwa biblioteki DLL jest pozycyjne i zawsze wykorzystasz; pozostałe o nazwie. W tym przypadku nazwanych parametrów domyślna wartość to false, dzięki czemu można pominąć. Zajrzyj do dokumentacji atrybutu Aby uzyskać informacji o domyślnych wartości parametrów.  
  
### <a name="attribute-targets"></a>Docelowe atrybuty  
 *Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut. Na przykład atrybut mogą dotyczyć klasy, konkretną metodę lub całego zestawu. Domyślnie atrybut stosuje się do elementu, który poprzedza. Ale można także jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody, lub jako parametr lub wartość zwracaną.  
  
 Aby jawnie określić element docelowy atrybutu, użyj następującej składni:  
  
```vb  
<target : attribute-list>  
```  
  
 Lista możliwych `target` wartości zostały przedstawione w poniższej tabeli.  
  
|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|  
|------------------|----------------|  
|`assembly`|Cały zespół|  
|`module`|Bieżącego zestawu modułu (który jest inny niż w Module języka Visual Basic)|  
  
 Poniższy przykład pokazuje, jak zastosować atrybutów do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [wspólne atrybuty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Najczęstsze zastosowania dla atrybutów  
 Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:  
  
- Oznaczanie metod za pomocą `WebMethod` atrybutów w usługach sieci Web, aby wskazać, że metoda powinna być wywoływane za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.  
  
- Opisujących sposób organizowania parametry metody podczas współpracy z kodu natywnego. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
- Opisujących właściwości modelu COM dla klasy, metody i interfejsy.  
  
- Wywoływanie niezarządzanego kodu za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.  
  
- Opisujące zestaw pod względem tytułu, wersji, opis lub znak towarowy.  
  
- Opisujących członków klasy do serializacji na potrzeby stanu trwałego.  
  
- Opisujących sposób mapowania między elementy członkowskie klasy i węzłów XML do serializacji XML.  
  
- Opisujących wymagania dotyczące zabezpieczeń dla metod.  
  
- Określanie właściwości używane do wymuszania zabezpieczeń.  
  
- Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje ułatwia debugowanie.  
  
- Uzyskiwanie informacji o obiekcie wywołującym metodę.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [Instrukcje: Tworzenie złożenia C/C++ za pomocą atrybutów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [Atrybuty wspólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
