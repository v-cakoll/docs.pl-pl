---
title: Atrybuty (C#)
ms.date: 04/26/2018
ms.openlocfilehash: c33d93a4af91e0c61546e8d51ab470f2889c095c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214150"
---
# <a name="attributes-c"></a>Atrybuty (C#)

Atrybuty zawierają zaawansowaną metodą kojarzenia metadanych lub informacji deklaratywne, przy użyciu kodu (zestawy, typy, metody, właściwości i tak dalej). Po atrybutu jest skojarzony z jednostką program, ten atrybut można wykonywać zapytania w czasie wykonywania za pomocą technikę o nazwie *odbicia*. Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../reflection.md).

Atrybuty mają następujące właściwości:

- Atrybuty dodawania metadanych do programu. *Metadane* obejmuje informacje dotyczące typów zdefiniowanych w programie. Wszystkie zestawy .NET zawierają określony zestaw metadane opisujące typy i elementy członkowskie typu zdefiniowane w zestawie. Możesz dodać atrybuty niestandardowe, aby określić dodatkowe informacje, która jest wymagana. Aby uzyskać więcej informacji znajduje się pozycja [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md).
- Jeden lub więcej atrybutów mogą dotyczyć całego zestawów, modułów lub mniejszych elementów programów, takich jak klasy i właściwości.
- Atrybuty można zaakceptować argumentów w taki sam sposób jak metody i właściwości.
- Program można sprawdzić swój własny metadanych lub metadanych w innych programach przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Przy użyciu atrybutów

Atrybuty można umieścić w praktycznie dowolnej deklaracji, chociaż określony atrybut może ograniczyć typy deklaracji, na których jest on prawidłowy. W C# należy określić atrybut, umieszczając nazwę atrybutu, ujęte w nawiasy kwadratowe ([]) powyżej deklaracji jednostki, której dotyczy.

W tym przykładzie <xref:System.SerializableAttribute> atrybut jest używany do stosowania szczególne właściwości do klasy:

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Metody z atrybutem <xref:System.Runtime.InteropServices.DllImportAttribute> jest zadeklarowana, jak w poniższym przykładzie:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Więcej niż jeden atrybut można umieścić w deklaracji, co ilustruje poniższy przykład:

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Niektóre atrybuty można określić więcej niż jeden raz dla danej jednostki. Na przykład multiuse — atrybut <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Zgodnie z Konwencją wszystkie nazwy atrybutu kończą się wyrazem "Atrybut", aby odróżnić je od innych elementów w bibliotekach .NET. Nie musisz jednak określić sufiks atrybutu, korzystając z atrybutów w kodzie. Na przykład `[DllImport]` jest odpowiednikiem `[DllImportAttribute]`, ale `DllImportAttribute` jest rzeczywistą nazwą atrybutu w bibliotece klas programu .NET Framework.

### <a name="attribute-parameters"></a>Parametry atrybutów

Wiele atrybutów ma parametry, które mogą być pozycyjne, bez nazwy lub nazwane. Wszystkie parametry pozycyjne musi być określona w określonej kolejności i nie może być pominięty. Parametry nazwane są opcjonalne i może być określony w dowolnej kolejności. Parametry pozycyjne są określony jako pierwszy. Na przykład te trzy atrybuty są równoważne:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

Pierwszy parametr, nazwa biblioteki DLL jest pozycyjne i zawsze wykorzystasz; pozostałe o nazwie. W tym przypadku nazwanych parametrów domyślna wartość to false, dzięki czemu można pominąć. Parametry pozycyjne odpowiadają parametrom atrybut konstruktora. Nazwana lub opcjonalne parametry odnoszą się do właściwości lub pola atrybutu. Zajrzyj do dokumentacji atrybutu Aby uzyskać informacji o domyślnych wartości parametrów.

### <a name="attribute-targets"></a>Docelowe atrybuty

*Docelowej* atrybutu jest jednostki, której dotyczy ten atrybut. Na przykład atrybut mogą dotyczyć klasy, konkretną metodę lub całego zestawu. Domyślnie atrybut stosuje się do elementu, który poprzedza. Ale można także jawnie zidentyfikować, na przykład, czy atrybut jest stosowany do metody, lub jako parametr lub wartość zwracaną.

Aby jawnie określić element docelowy atrybutu, użyj następującej składni:

```csharp
[target : attribute-list]
```

Lista możliwych `target` wartości zostały przedstawione w poniższej tabeli.

|Wartość docelowa|Informacje zawarte w tym artykule dotyczą|
|------------------|----------------|
|`assembly`|Cały zespół|
|`module`|Bieżącego zestawu modułu|
|`field`|Pole w klasie lub strukturze|
|`event`|Zdarzenie|
|`method`|Metoda lub `get` i `set` Akcesory właściwości|
|`param`|Parametry metody lub `set` parametry metody dostępu właściwości|
|`property`|Właściwość|
|`return`|Zwraca wartość metody, właściwości indeksatora lub `get` metody dostępu właściwości|
|`type`|Struktury, klasy, interfejsu, enum lub delegata|

Należy określić `field` wartość docelową, aby zastosować atrybut do pola pomocniczego utworzone dla [automatycznie implementowana właściwość](../../../properties.md).

Poniższy przykład pokazuje, jak zastosować atrybutów do zestawów i modułów. Aby uzyskać więcej informacji, zobacz [atrybuty wspólne (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Poniższy przykład pokazuje, jak zastosować atrybutów do metod i parametry metody, a metoda zwraca wartości w języku C#.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Niezależnie od tego, obiekty docelowe, na którym `ValidatedContract` zdefiniowano był prawidłowy, `return` docelowy musi być określona, nawet wtedy, gdy `ValidatedContract` zostały zdefiniowane w celu mają zastosowanie tylko do zwracania wartości. Innymi słowy, kompilator nie będzie używać `AttributeUsage` informacje pozwalające rozwiązać niejednoznaczny atrybut elementów docelowych. Aby uzyskać więcej informacji, zobacz [AttributeUsage (C#)](attributeusage.md).

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

- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)  
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)  
- [Porady: tworzenie złożenia C/C++ za pomocą atrybutów (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Atrybuty wspólne (C#)](common-attributes.md)  
- [Informacje o wywołującym (C#)](../caller-information.md)  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../index.md)  
- [Odbicie (C#)](../reflection.md)  
- [Atrybuty](../../../../standard/attributes/index.md)  
- [Przy użyciu atrybutów w języku C#](../../../tutorials/attributes.md)  
