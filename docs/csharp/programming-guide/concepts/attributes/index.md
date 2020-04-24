---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 0379bb76cf18ff836bd14aafb9cb97c30aee8ec7
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645485"
---
# <a name="attributes-c"></a>Atrybuty (C#)

Atrybuty zapewniają zaawansowaną metodę kojarzenia metadanych lub informacji deklaratywnych z kodem (zestawy, typy, metody, właściwości i tak dalej). Po skojarzeniu atrybutu z encją programu, atrybut można zbadać w czasie wykonywania przy użyciu techniki zwanej *odbiciem*. Aby uzyskać więcej informacji, zobacz [Odbicie (C#)](../reflection.md).

Atrybuty mają następujące właściwości:

- Atrybuty dodają metadane do programu. *Metadane* to informacje o typach zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadanych, który opisuje typy i elementy członkowskie typu zdefiniowane w zestawie. Można dodać atrybuty niestandardowe, aby określić wszelkie dodatkowe informacje, które są wymagane. Aby uzyskać więcej informacji, zobacz Tworzenie [atrybutów niestandardowych (C#)](creating-custom-attributes.md).
- Można zastosować jeden lub więcej atrybutów do całych zestawów, modułów lub mniejszych elementów programu, takich jak klasy i właściwości.
- Atrybuty mogą akceptować argumenty w taki sam sposób jak metody i właściwości.
- Program może sprawdzić własne metadane lub metadane w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Korzystanie z atrybutów

Atrybuty mogą być umieszczane w większości dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest prawidłowy. W języku C#można określić atrybut, umieszczając nazwę atrybutu ujętego w nawiasach kwadratowych ([]) nad deklaracją jednostki, do której ma zastosowanie.

W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania określonej cechy do klasy:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metoda z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana w następującym przykładzie:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Więcej niż jeden atrybut można umieścić w deklaracji, jak pokazano w poniższym przykładzie:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki. Przykładem takiego atrybutu wielofunkcyjnego <xref:System.Diagnostics.ConditionalAttribute>jest:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Zgodnie z konwencją wszystkie nazwy atrybutów kończą się słowem "Atrybut", aby odróżnić je od innych elementów w bibliotekach .NET. Jednak nie trzeba określać sufiks atrybutu podczas korzystania z atrybutów w kodzie. Na przykład `[DllImport]` jest `[DllImportAttribute]`odpowiednikiem `DllImportAttribute` , ale jest rzeczywistą nazwą atrybutu w bibliotece klas .NET Framework.

### <a name="attribute-parameters"></a>Parametry atrybutu

Wiele atrybutów ma parametry, które mogą być pozycyjne, nienazwane lub nazwane. Wszelkie parametry pozycyjne muszą być określone w określonej kolejności i nie można ich pominąć. Nazwane parametry są opcjonalne i można je określić w dowolnej kolejności. Parametry pozycyjne są określone jako pierwsze. Na przykład te trzy atrybuty są równoważne:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

Pierwszy parametr, nazwa biblioteki DLL, jest pozycyjny i zawsze jest pierwszy; pozostałe są nazwane. W takim przypadku oba nazwane parametry domyślnie false, więc mogą być pominięte. Parametry pozycyjne odpowiadają parametrom konstruktora atrybutów. Parametry nazwane lub opcjonalne odpowiadają właściwościom lub polom atrybutu. Informacje na temat domyślnych wartości parametrów można znaleźć w dokumentacji poszczególnych atrybutów.

### <a name="attribute-targets"></a>Docelowe atrybuty

Obiekt *docelowy* atrybutu jest jednostką, której dotyczy atrybut. Na przykład atrybut może mieć zastosowanie do klasy, określonej metody lub całego zestawu. Domyślnie atrybut ma zastosowanie do elementu, który następuje po nim. Ale można również jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody lub do jego parametru lub do jego wartości zwracanej.

Aby jawnie zidentyfikować obiekt docelowy atrybutu, należy użyć następującej składni:

```csharp
[target : attribute-list]
```

Lista możliwych `target` wartości jest przedstawiona w poniższej tabeli.

|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|
|------------------|----------------|
|`assembly`|Cały zespół|
|`module`|Obecny moduł montażowy|
|`field`|Pole w klasie lub strukturze|
|`event`|Wydarzenie|
|`method`|Metody `get` lub `set` akcesory właściwości|
|`param`|Parametry metody `set` lub parametry akcesora właściwości|
|`property`|Właściwość|
|`return`|Zwraca wartość metody, indeksatora `get` właściwości lub akcesora właściwości|
|`type`|Struktura, klasa, interfejs, wyliczenia lub delegata|

Można określić `field` wartość docelową, aby zastosować atrybut do pola zapasowego utworzonego dla [właściwości automatycznie zaimplementowane](../../../properties.md).

W poniższym przykładzie pokazano, jak zastosować atrybuty do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [Wspólne atrybuty (C#)](../../../language-reference/attributes/global.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Poniższy przykład pokazuje, jak zastosować atrybuty do metod, parametrów metody i wartości zwracanej metody w języku C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Niezależnie od docelowych, `ValidatedContract` dla których jest `return` zdefiniowany jako prawidłowy, `ValidatedContract` cel musi być określony, nawet jeśli zostały zdefiniowane do zastosowania tylko do zwracanych wartości. Innymi słowy kompilator nie `AttributeUsage` będzie używać informacji do rozpoznawania niejednoznacznych docelowych atrybutów. Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](../../../language-reference/attributes/general.md).

## <a name="common-uses-for-attributes"></a>Typowe zastosowania atrybutów

Poniższa lista zawiera kilka typowych zastosowań atrybutów w kodzie:

- Metody znakowania `WebMethod` przy użyciu atrybutu w usługach sieci Web, aby wskazać, że metoda powinna być wywoływana za pośrednictwem protokołu SOAP. Aby uzyskać więcej informacji, zobacz <xref:System.Web.Services.WebMethodAttribute>.
- Opisujące sposób organizowania parametrów metody podczas współpracy z kodem macierzystym. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Opisujące właściwości COM dla klas, metod i interfejsów.
- Wywoływanie kodu niezarządzanego <xref:System.Runtime.InteropServices.DllImportAttribute> przy użyciu klasy.
- Opisujące twój montaż pod względem tytułu, wersji, opisu lub znaku towarowego.
- Opisujące, którzy członkowie klasy do serializacji dla trwałości.
- Opisujące sposób mapowania między członkami klasy i węzłów XML dla serializacji XML.
- Opisujące wymagania dotyczące zabezpieczeń dla metod.
- Określanie właściwości używanych do wymuszania zabezpieczeń.
- Kontrolowanie optymalizacji przez kompilator just-in-time (JIT), dzięki czemu kod pozostaje łatwy do debugowania.
- Uzyskiwanie informacji o wywołującym do metody.

## <a name="related-sections"></a>Powiązane sekcje

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)  
- [Jak utworzyć unię C/C++ przy użyciu atrybutów (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Typowe atrybuty (C#)](../../../language-reference/attributes/global.md)  
- [Informacje o dzwoniącym (C#)](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../../index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Korzystanie z atrybutów w języku C #](../../../tutorials/attributes.md)
