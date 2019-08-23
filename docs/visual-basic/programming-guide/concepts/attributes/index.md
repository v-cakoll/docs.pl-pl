---
title: Omówienie atrybutów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: c799b9be9b936beadde28374bd9882ebc6e2d9a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966319"
---
# <a name="attributes-overview-visual-basic"></a>Omówienie atrybutów (Visual Basic)
Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub deklaracyjne informacje z kodem (zestawy, typy, metody, właściwości i tak dalej). Gdy atrybut jest skojarzony z jednostką programu, atrybut może być badany w czasie wykonywania przy użyciu techniki o nazwie odbicie. Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
 Atrybuty mają następujące właściwości:  
  
- Atrybuty dodają metadane do programu. *Metadane* są informacjami o typach zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie. Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane. Aby uzyskać więcej informacji, zobacz temat [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
- Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.  
  
- Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.  
  
- Program może przeanalizować własne metadane lub metadane w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Korzystanie z atrybutów  
 Atrybuty mogą być umieszczane w większości każdej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy. W Visual Basic atrybut jest ujęty w nawiasy kątowe\< (>). Musi znajdować się bezpośrednio przed elementem, do którego jest stosowany, w tym samym wierszu.  
  
 W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do zastosowania konkretnej cechy klasy:  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana w następujący sposób:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 W deklaracji można umieścić więcej niż jeden atrybut:  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 Niektóre atrybuty można określić więcej niż raz dla danej jednostki. Przykładem takiego atrybutu Multiuse jest <xref:System.Diagnostics.ConditionalAttribute>:  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
> Według Konwencji wszystkie nazwy atrybutów kończą się słowem "Attribute", aby odróżnić je od innych elementów w .NET Framework. Nie trzeba jednak określać sufiksu atrybutu podczas używania atrybutów w kodzie. Na przykład `[DllImport]` jest równoważne z `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w .NET Framework.  
  
### <a name="attribute-parameters"></a>Parametry atrybutu  
 Wiele atrybutów ma parametry, które mogą mieć położenie, nienazwane lub nazwane. Wszystkie parametry pozycyjne muszą być określone w określonej kolejności i nie mogą być pomijane; parametry nazwane są opcjonalne i można je określić w dowolnej kolejności. Parametry pozycyjne są określone jako pierwsze. Na przykład te trzy atrybuty są równoważne:  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 Pierwszy parametr, nazwa biblioteki DLL, jest położeniem i zawsze jest pierwszy. inne osoby mają nazwę. W tym przypadku oba nazwane parametry domyślnie mają wartość false, więc można je pominąć. Informacje dotyczące domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.  
  
### <a name="attribute-targets"></a>Docelowe atrybuty  
 *Obiektem docelowym* atrybutu jest jednostka, do której odnosi się ten atrybut. Na przykład, atrybut może dotyczyć klasy, konkretnej metody lub całego zestawu. Domyślnie atrybut ma zastosowanie do elementu, który poprzedza. Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.  
  
 Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:  
  
```vb  
<target : attribute-list>  
```  
  
 Lista możliwych `target` wartości jest pokazana w poniższej tabeli.  
  
|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|  
|------------------|----------------|  
|`assembly`|Cały zestaw|  
|`module`|Bieżący moduł zestawu (który różni się od modułu Visual Basic)|  
  
 Poniższy przykład pokazuje, jak zastosować atrybuty do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a>Typowe zastosowania atrybutów  
 Poniższa lista zawiera kilka typowych zastosowania atrybutów w kodzie:  
  
- Oznaczanie metod przy `WebMethod` użyciu atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.  
  
- Opis sposobu organizowania parametrów metody podczas współdziałania z kodem natywnym. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
- Opisywanie właściwości modelu COM dla klas, metod i interfejsów.  
  
- Wywoływanie kodu niezarządzanego za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.  
  
- Opisywanie zestawu pod względem tytułu, wersji, opisu lub znaku towarowego.  
  
- Opisywanie elementów członkowskich klasy do serializacji dla trwałości.  
  
- Opis sposobu mapowania między elementami członkowskimi klasy i węzłami XML na potrzeby serializacji XML.  
  
- Opisywanie wymagań dotyczących zabezpieczeń dla metod.  
  
- Określanie charakterystyki służącej do wymuszania zabezpieczeń.  
  
- Kontrolowanie optymalizacji przez kompilator just-in-Time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.  
  
- Uzyskiwanie informacji o wywołującym do metody.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
- [Instrukcje: Utwórz element C/C++ Union przy użyciu atrybutów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
- [Atrybuty wspólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
- [Informacje o wywołującym (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
