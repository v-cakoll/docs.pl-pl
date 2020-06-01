---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 358285a39f72ad3ddf1b265e20b443308375d074
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241581"
---
# <a name="attributes-c"></a>Atrybuty (C#)

Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub deklaracyjne informacje z kodem (zestawy, typy, metody, właściwości i tak dalej). Gdy atrybut jest skojarzony z jednostką programu, atrybut może być badany w czasie wykonywania przy użyciu techniki o nazwie *odbicie*. Aby uzyskać więcej informacji, zobacz [odbicie (C#)](../reflection.md).

Atrybuty mają następujące właściwości:

- Atrybuty dodają metadane do programu. *Metadane* są informacjami o typach zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie. Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane. Aby uzyskać więcej informacji, zobacz temat [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md).
- Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.
- Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.
- Program może przeanalizować własne metadane lub metadane w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Używanie atrybutów

Atrybuty mogą być umieszczane w większości każdej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy. W języku C# należy określić atrybut poprzez umieszczenie nazwy atrybutu w nawiasach kwadratowych ([]) powyżej deklaracji jednostki, do której ma zastosowanie.

W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do zastosowania konkretnej cechy klasy:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana jak w poniższym przykładzie:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Więcej niż jeden atrybut może być umieszczony w deklaracji, jak pokazano w poniższym przykładzie:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Niektóre atrybuty można określić więcej niż raz dla danej jednostki. Przykładem takiego atrybutu Multiuse jest <xref:System.Diagnostics.ConditionalAttribute> :

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Według Konwencji wszystkie nazwy atrybutów kończą się słowem "Attribute", aby odróżnić je od innych elementów w bibliotekach platformy .NET. Nie trzeba jednak określać sufiksu atrybutu podczas używania atrybutów w kodzie. Na przykład `[DllImport]` jest równoważne z `[DllImportAttribute]` , ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas .NET.

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

Lista możliwych `target` wartości jest pokazana w poniższej tabeli.

|Wartość docelowa|Dotyczy|
|------------------|----------------|
|`assembly`|Cały zestaw|
|`module`|Bieżący moduł zestawu|
|`field`|Pole w klasie lub strukturze|
|`event`|Zdarzenie|
|`method`|Metody dostępu metod lub `get` `set` właściwości|
|`param`|Parametry metody lub `set` parametry metod dostępu do właściwości|
|`property`|Właściwość|
|`return`|Wartość zwracana metody, indeksatora właściwości lub metody dostępu do `get` właściwości|
|`type`|Struct, Class, Interface, enum lub Delegate|

Należy określić `field` wartość docelową, aby zastosować atrybut do pola zapasowego utworzonego dla właściwości, która jest [implementowana](../../../properties.md).

Poniższy przykład pokazuje, jak zastosować atrybuty do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [Common Attributes (C#)](../../../language-reference/attributes/global.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Poniższy przykład pokazuje, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanych metody w języku C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Bez względu na to, w którym `ValidatedContract` miejscu docelowym jest zdefiniowane prawidłowe, należy `return` określić element docelowy, nawet jeśli `ValidatedContract` zostały zdefiniowane do zastosowania tylko do wartości zwracanych. Innymi słowy kompilator nie będzie używać `AttributeUsage` informacji do rozwiązywania niejednoznacznych obiektów docelowych atrybutu. Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](../../../language-reference/attributes/general.md).

## <a name="common-uses-for-attributes"></a>Typowe zastosowania atrybutów

Poniższa lista zawiera kilka typowych zastosowania atrybutów w kodzie:

- Oznaczanie metod przy użyciu `WebMethod` atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.
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

- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)  
- [Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Atrybuty wspólne (C#)](../../../language-reference/attributes/global.md)  
- [Informacje o wywołującym (C#)](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Używanie atrybutów w C #](../../../tutorials/attributes.md)
