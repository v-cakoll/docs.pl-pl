---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399750"
---
# <a name="attributes-c"></a>Atrybuty (C#)

Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub informacji deklaratywnych z kodem (zestawy, typy, metody, właściwości i tak dalej). Po skojarzonez atrybutz encji programu, atrybut można zbadać w czasie wykonywania przy użyciu techniki o nazwie *odbicie*. Aby uzyskać więcej informacji, zobacz [Odbicie (C#)](../reflection.md).

Atrybuty mają następujące właściwości:

- Atrybuty dodają metadane do programu. *Metadane* to informacje o typach zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych opisujący typy i elementy członkowskie typu zdefiniowane w zestawie. Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane. Aby uzyskać więcej informacji, zobacz [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md).
- Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.
- Atrybuty mogą akceptować argumenty w taki sam sposób, jak metody i właściwości.
- Program może sprawdzić własne metadane lub metadane w innych programach za pomocą odbicia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Korzystanie z atrybutów

Atrybuty mogą być umieszczane na większości dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest prawidłowy. W języku C#, należy określić atrybut, umieszczając nazwę atrybutu ujęty w nawiasach kwadratowych ([]) nad deklaracją jednostki, do której ma zastosowanie.

W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do zastosowania określonej cechy do klasy:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana w następujący sposób w poniższym przykładzie:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Więcej niż jeden atrybut można umieścić na deklaracji, jak pokazano w poniższym przykładzie:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki. Przykładem takiego atrybutu wielokrotnego <xref:System.Diagnostics.ConditionalAttribute>użytku jest:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Zgodnie z konwencją wszystkie nazwy atrybutów kończą się słowem "Atrybut", aby odróżnić je od innych elementów w bibliotekach .NET. Jednak nie trzeba określać sufiksatrybutatrybutu atrybutu podczas używania atrybutów w kodzie. Na przykład `[DllImport]` jest `[DllImportAttribute]`odpowiednikiem `DllImportAttribute` , ale jest rzeczywistą nazwą atrybutu w bibliotece klas .NET Framework.

### <a name="attribute-parameters"></a>Parametry atrybutu

Wiele atrybutów ma parametry, które mogą być pozycyjne, nienazwane lub nazwane. Wszelkie parametry pozycyjne muszą być określone w określonej kolejności i nie można ich pominąć. Nazwane parametry są opcjonalne i mogą być określone w dowolnej kolejności. Parametry pozycyjne są określone jako pierwsze. Na przykład te trzy atrybuty są równoważne:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

Pierwszy parametr, nazwa dll, jest pozycyjny i zawsze jest na pierwszym miejscu; pozostałe są nazwane. W takim przypadku oba nazwane parametry domyślnie false, więc można je pominąć. Parametry pozycyjne odpowiadają parametrom konstruktora atrybutu. Parametry nazwane lub opcjonalne odpowiadają właściwościom lub polom atrybutu. Informacje na temat domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.

### <a name="attribute-targets"></a>Docelowe atrybuty

*Obiektdocelowy* atrybutu jest jednostką, do której stosuje się atrybut. Na przykład atrybut może dotyczyć klasy, określonej metody lub całego zestawu. Domyślnie atrybut stosuje się do elementu, który następuje po nim. Ale można również jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody lub jej parametru lub do jego wartości zwracanej.

Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:

```csharp
[target : attribute-list]
```

Lista możliwych `target` wartości jest wyświetlana w poniższej tabeli.

|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|
|------------------|----------------|
|`assembly`|Cały montaż|
|`module`|Moduł montażu prądu|
|`field`|Pole w klasie lub strukturze|
|`event`|Wydarzenie|
|`method`|Metody `get` lub `set` akcesory własności|
|`param`|Parametry metody `set` lub parametry akcesora właściwości|
|`property`|Właściwość|
|`return`|Zwracana wartość metody, indeksatora właściwości lub `get` akcesora właściwości|
|`type`|Struktura, klasa, interfejs, wyliczenie lub delegowanie|

Należy określić `field` wartość docelową, aby zastosować atrybut do pola zapasowego utworzonego dla [właściwości implementowane automatycznie](../../../properties.md).

W poniższym przykładzie pokazano, jak zastosować atrybuty do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [Wspólne atrybuty (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

W poniższym przykładzie pokazano, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanych metody w języku C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Niezależnie od celów, `ValidatedContract` dla których jest zdefiniowany jako prawidłowy, `return` cel `ValidatedContract` musi być określony, nawet jeśli zostały zdefiniowane do stosowania tylko do wartości zwracanych. Innymi słowy kompilator nie `AttributeUsage` będzie używać informacji do rozpoznawania niejednoznacznych obiektów docelowych atrybutów. Aby uzyskać więcej informacji, zobacz [Użycie atrybutów (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Typowe zastosowania atrybutów

Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:

- Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.
- Opisujące sposób organizowania parametrów metody podczas współdziałania z kodem macierzystym. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Opisujące właściwości COM dla klas, metod i interfejsów.
- Wywołanie kodu niezarządzanego przy użyciu <xref:System.Runtime.InteropServices.DllImportAttribute> klasy.
- Opisując episcie twojego zestawu pod względem tytułu, wersji, opisu lub znaku towarowego.
- Opisujące, które elementy członkowskie klasy do serializacji dla trwałości.
- Opisujące sposób mapowania między członkami klasy i węzłów XML dla serializacji XML.
- Opisujące wymagania dotyczące zabezpieczeń dla metod.
- Określanie cech używanych do wymuszania zabezpieczeń.
- Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.
- Uzyskiwanie informacji o obiekcie wywołującym do metody.

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)  
- [Jak utworzyć związek C/C++ przy użyciu atrybutów (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Typowe atrybuty (C#)](common-attributes.md)  
- [Informacje o obiekcie wywołującym (C#)](../caller-information.md)  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../../index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Korzystanie z atrybutów w C #](../../../tutorials/attributes.md)
