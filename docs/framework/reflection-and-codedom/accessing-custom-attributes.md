---
title: "Uzyskiwanie dostępu do atrybutów niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0980488f3093bfcaedc730bac126b1b5b6505187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-custom-attributes"></a>Uzyskiwanie dostępu do atrybutów niestandardowych
Po atrybuty zostały skojarzone z elementów programu, odbicia może służyć do badania ich istnienie i wartości. W programie .NET Framework w wersji 1.0, 1.1 atrybuty niestandardowe są sprawdzane w kontekstu wykonywania. .NET Framework w wersji 2.0 zapewnia nowy kontekst ładowania kontekstu reflection-only, którego można użyć do sprawdzenia kod, który nie może zostać załadowany do wykonania.  
  
## <a name="the-reflection-only-context"></a>Kontekstu Reflection-Only  
 Nie można wykonać kod ładowane do kontekstu reflection-only. Oznacza to, że nie można tworzyć wystąpień atrybutów niestandardowych, ponieważ który wymaga wykonywania ich konstruktorów. Aby załadować i sprawdź, czy atrybuty niestandardowe w kontekstu reflection-only, użyj <xref:System.Reflection.CustomAttributeData> klasy. Wystąpienia tej klasy można uzyskać za pomocą odpowiedniego przeciążenia statycznych <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody. Zobacz [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Kontekst wykonywania  
 Metody main odbicia atrybutów kontekstu wykonywania zapytania są <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> i <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Dostępność atrybut niestandardowy jest sprawdzana względem zestawu, w której jest dołączony. Jest to równoważne sprawdzanie, czy metody dla typu w zestawie, w której jest dołączona atrybutu niestandardowego można wywołać konstruktora atrybutu niestandardowego.  
  
 Metody, takie jak <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> Sprawdź widoczność i dostępności argumentu typu. Tylko kod w zestawie, którą zawiera typ zdefiniowany przez użytkownika można pobrać atrybutu niestandardowego o tego typu za pomocą **GetCustomAttributes**.  
  
 W poniższym przykładzie C# to wzorzec projektowania typowe atrybutu niestandardowego. Zastosowano modelu odbicia atrybutu niestandardowego środowiska wykonawczego.  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Jeśli środowisko wykonawcze próbuje pobrać atrybutów niestandardowych dla typu atrybutu niestandardowego publicznego <xref:System.ComponentModel.DescriptionAttribute> dołączony do **GetLanguage** metoda wykonuje następujące akcje:  
  
1.  Środowisko uruchomieniowe sprawdza, czy argument typu **DescriptionAttribute** do **Type.GetCustomAttributes**(typ *typu*) nie jest publiczny i dlatego jest widoczny i jest dostępny.  
  
2.  Środowisko uruchomieniowe sprawdza, czy typ zdefiniowany przez użytkownika **MyDescriptionAttribute** która jest pochodną **DescriptionAttribute** jest widoczny i jest dostępny w ramach **System.Web.DLL**zestawu, w której jest podłączony do metody **GetLanguage**().  
  
3.  Środowisko uruchomieniowe sprawdza, czy konstruktora **MyDescriptionAttribute** jest widoczny i jest dostępny w ramach **System.Web.DLL** zestawu.  
  
4.  Środowisko uruchomieniowe wywołania konstruktora **MyDescriptionAttribute** z parametrami atrybutu niestandardowego i zwraca nowy obiekt do obiektu wywołującego.  
  
 Atrybut niestandardowy model odbicia można wyciek wystąpień typów zdefiniowanych przez użytkownika spoza zestawu, w którym jest zdefiniowany typ. To nie różni się od elementów członkowskich w Biblioteka środowiska uruchomieniowego systemu, które zwracają wystąpień typów zdefiniowanych przez użytkownika, takie jak <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tablicę **RuntimeMethodInfo** obiektów. Aby zapobiec klienta z odnajdowania informacji o typie atrybutów niestandardowych zdefiniowanych przez użytkownika, należy zdefiniować elementów członkowskich typu jako niepubliczny.  
  
 W poniższym przykładzie pokazano podstawową metodą do uzyskania dostępu do atrybutów niestandardowych za pomocą odbicia.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
