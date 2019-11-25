---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141564"
---
# <a name="attributes-c"></a>Atrybuty (C#)

Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub deklaracyjne informacje z kodem (zestawy, typy, metody, właściwości i tak dalej). Gdy atrybut jest skojarzony z jednostką programu, atrybut może być badany w czasie wykonywania przy użyciu techniki o nazwie *odbicie*. Aby uzyskać więcej informacji, zobacz [odbicie (C#)](../reflection.md).

Atrybuty mają następujące właściwości:

- Atrybuty dodają metadane do programu. *Metadane* są informacjami o typach zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie. Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane. Aby uzyskać więcej informacji, zobacz temat [Tworzenie atrybutów niestandardowychC#()](creating-custom-attributes.md).
- Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.
- Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.
- Program może przeanalizować własne metadane lub metadane w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutówC#przy użyciu odbicia ()](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Używanie atrybutów

Atrybuty mogą być umieszczane w większości każdej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy. W C#programie należy określić atrybut, umieszczając nazwę atrybutu ujętą w nawiasy kwadratowe ([]) powyżej deklaracji jednostki, do której ma zastosowanie.

W tym przykładzie atrybut <xref:System.SerializableAttribute> jest używany do zastosowania konkretnej cechy klasy:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana jak w poniższym przykładzie:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Więcej niż jeden atrybut może być umieszczony w deklaracji, jak pokazano w poniższym przykładzie:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Niektóre atrybuty można określić więcej niż raz dla danej jednostki. Przykładem takiego atrybutu Multiuse jest <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Według Konwencji wszystkie nazwy atrybutów kończą się słowem "Attribute", aby odróżnić je od innych elementów w bibliotekach platformy .NET. Nie trzeba jednak określać sufiksu atrybutu podczas używania atrybutów w kodzie. Na przykład `[DllImport]` jest równoważne `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas .NET Framework.

### <a name="attribute-parameters"></a>Parametry atrybutu

Wiele atrybutów ma parametry, które mogą mieć położenie, nienazwane lub nazwane. Wszystkie parametry pozycyjne muszą być określone w określonej kolejności i nie mogą być pominięte. Parametry nazwane są opcjonalne i można je określić w dowolnej kolejności. Parametry pozycyjne są określone jako pierwsze. Na przykład te trzy atrybuty są równoważne:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

Pierwszy parametr, nazwa biblioteki DLL, jest położeniem i zawsze jest pierwszy. inne osoby mają nazwę. W tym przypadku oba nazwane parametry domyślnie mają wartość false, więc można je pominąć. Parametry pozycyjne odpowiadają parametrom konstruktora atrybutu. Parametry nazwane lub opcjonalne odpowiadają właściwościom lub polom atrybutu. Informacje dotyczące domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.

### <a name="attribute-targets"></a>Docelowe atrybuty

*Obiektem docelowym* atrybutu jest jednostka, do której odnosi się ten atrybut. Na przykład, atrybut może dotyczyć klasy, konkretnej metody lub całego zestawu. Domyślnie atrybut ma zastosowanie do elementu, który następuje po nim. Ale można również jawnie określić, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.

Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:

```csharp
[target : attribute-list]
```

Lista możliwych wartości `target` przedstawiono w poniższej tabeli.

|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|
|------------------|----------------|
|`assembly`|Cały zestaw|
|`module`|Bieżący moduł zestawu|
|`field`|Pole w klasie lub strukturze|
|`event`|Zdarzenie|
|`method`|Metody dostępu do właściwości metod lub `get` i `set`|
|`param`|Parametry metody lub `set` parametry dostępu do właściwości|
|`property`|Właściwość|
|`return`|Wartość zwracana metody, indeksatora właściwości lub właściwości `get`|
|`type`|Struct, Class, Interface, enum lub Delegate|

Należy określić wartość docelową `field`, aby zastosować atrybut do pola zapasowego utworzonego dla właściwości, która jest [implementowana](../../../properties.md).

Poniższy przykład pokazuje, jak zastosować atrybuty do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [Common AttributesC#()](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Poniższy przykład pokazuje, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanych metody w C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Niezależnie od obiektów docelowych, w których `ValidatedContract` jest zdefiniowany jako prawidłowy, należy określić element docelowy `return`, nawet jeśli `ValidatedContract` zostały zdefiniowane do zastosowania tylko do wartości zwracanych. Innymi słowy kompilator nie będzie używać `AttributeUsage` informacji do rozwiązywania niejednoznacznych obiektów docelowych atrybutu. Aby uzyskać więcej informacji, zobacz [AttributeUsageC#()](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Typowe zastosowania atrybutów

Poniższa lista zawiera kilka typowych zastosowania atrybutów w kodzie:

- Oznaczanie metod przy użyciu atrybutu `WebMethod` w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.
- Opis sposobu organizowania parametrów metody podczas współdziałania z kodem natywnym. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Opisywanie właściwości modelu COM dla klas, metod i interfejsów.
- Wywoływanie kodu niezarządzanego za pomocą klasy <xref:System.Runtime.InteropServices.DllImportAttribute>.
- Opisywanie zestawu pod względem tytułu, wersji, opisu lub znaku towarowego.
- Opisywanie elementów członkowskich klasy do serializacji dla trwałości.
- Opis sposobu mapowania między elementami członkowskimi klasy i węzłami XML na potrzeby serializacji XML.
- Opisywanie wymagań dotyczących zabezpieczeń dla metod.
- Określanie charakterystyki służącej do wymuszania zabezpieczeń.
- Kontrolowanie optymalizacji przez kompilator just-in-Time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.
- Uzyskiwanie informacji o wywołującym do metody.

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()](accessing-attributes-by-using-reflection.md)  
- [Jak utworzyć element C/C++ Union przy użyciu atrybutów ()C#](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Atrybuty wspólne (C#)](common-attributes.md)  
- [Informacje o obiekcieC#wywołującym ()](../caller-information.md)  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../index.md)
- [OdbicieC#()](../reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Używanie atrybutów wC#](../../../tutorials/attributes.md)
