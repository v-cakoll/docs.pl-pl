---
title: Uzyskiwanie dostępu do atrybutów niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 764b0d535413fc1e5e23a2e47221789aa807ff38
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321734"
---
# <a name="accessing-custom-attributes"></a>Uzyskiwanie dostępu do atrybutów niestandardowych
Po atrybuty zostały skojarzone z elementami program, odbicie może służyć do kwerendy ich istnienie i wartości. W .NET Framework w wersji 1.0 i 1.1 atrybuty niestandardowe są badane w kontekście wykonywania. .NET Framework w wersji 2.0 zapewnia nowy kontekst obciążenia kontekstu reflection-only, którego można użyć, aby sprawdzić kod, którego nie można załadować do wykonania.  
  
## <a name="the-reflection-only-context"></a>Kontekstu Reflection-Only  
 Nie można wykonać kod ładowane do kontekstu reflection-only. Oznacza to, że nie można utworzyć wystąpienia atrybutów niestandardowych, ponieważ wymagałoby, wykonywanie ich konstruktory. Aby załadować i zbadać atrybutów niestandardowych w kontekstu reflection-only, należy użyć <xref:System.Reflection.CustomAttributeData> klasy. Wystąpienia tej klasy można uzyskać za pomocą odpowiednich przeciążenia statycznych <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody. Zobacz [jak: Ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Kontekst wykonywania  
 Metody głównej odbicia do atrybutów zapytania w kontekście wykonania są <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> i <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Dostępność atrybut niestandardowy jest sprawdzany w odniesieniu do zestawu, w której jest dołączony. Jest to równoważne do sprawdzania, czy metoda w typie w zestawie, w której jest dołączony atrybut niestandardowy można wywołać konstruktora atrybutu niestandardowego.  
  
 Metody takie jak <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> Sprawdź widoczność i dostępność argument typu. Tylko do kodu w zestawie, który zawiera typ zdefiniowany przez użytkownika można pobrać atrybutu niestandardowego dla tego typu za pomocą **getcustomattributes —**.  
  
 Następujące C# przykładem jest wzorzec projektowy typowe atrybutu niestandardowego. Zawiera ono modelu odbicia atrybutu niestandardowego środowiska uruchomieniowego.  
  
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
  
 Jeśli środowisko wykonawcze próbuje pobrać atrybutów niestandardowych dla tego typu atrybutu niestandardowego publicznych <xref:System.ComponentModel.DescriptionAttribute> dołączone do **getlanguage —** metody wykonuje następujące czynności:  
  
1. Środowisko uruchomieniowe sprawdza, czy argument typu **DescriptionAttribute** do **Type.GetCustomAttributes**(typ *typu*) nie jest publiczny i dlatego jest widoczny i dostępny.  
  
2. Środowisko uruchomieniowe sprawdza, czy typ zdefiniowany przez użytkownika **MyDescriptionAttribute** , jest tworzony na podstawie **DescriptionAttribute** jest widoczny i dostępny w ramach **System.Web.DLL**zestawu, w której jest podłączony do metody **getlanguage —**().  
  
3. Środowisko uruchomieniowe sprawdza, czy konstruktora **MyDescriptionAttribute** jest widoczny i dostępny w ramach **System.Web.DLL** zestawu.  
  
4. Środowisko wykonawcze wywołuje konstruktor **MyDescriptionAttribute** z parametrami atrybutu niestandardowego i zwraca nowy obiekt do obiektu wywołującego.  
  
 Atrybut niestandardowy model odbicia mogą spowodować przeciek tych wystąpień typów zdefiniowanych przez użytkownika spoza zestawu, w którym typ jest zdefiniowany. To nie różni się od członków w bibliotece środowiska uruchomieniowego systemu, które zwracają wystąpień typów zdefiniowanych przez użytkownika, takie jak <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> tablicę **RuntimeMethodInfo** obiektów. Aby zapobiec klienta z odnajdywanie informacji o typie atrybutów niestandardowych zdefiniowanych przez użytkownika, należy zdefiniować członkom typów można niepublicznych.  
  
 Poniższy przykład pokazuje podstawowy sposób przy użyciu odbicia w celu uzyskania dostępu do atrybutów niestandardowych.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Zagadnienia dotyczące zabezpieczeń dla odbicia](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
