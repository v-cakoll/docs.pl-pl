---
title: 'Porady: ładowanie zestawów do domeny aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c560e2c5858de67442ccbcd18c8f92b142cc178d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119891"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Porady: ładowanie zestawów do domeny aplikacji
Istnieje kilka sposobów ładowania zestawu do domeny aplikacji. Zalecanym sposobem jest użycie `static` metody (`Shared` w Visual Basic) <xref:System.Reflection.Assembly.Load%2A> <xref:System.Reflection.Assembly?displayProperty=nameWithType> klasy. Inne sposoby ładowania zestawów obejmują:  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> Metoda <xref:System.Reflection.Assembly> klasy ładuje zestaw z uwzględnieniem jego lokalizacji pliku. Ładowanie zestawów za pomocą tej metody używa innego kontekstu ładowania.  
  
- Metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> ładują zestaw do kontekstu tylko odbicie. Zestawy ładowane do tego kontekstu mogą być badane, ale nie wykonywane, umożliwiając badanie zestawów przeznaczonych dla innych platform. Zobacz [instrukcje: ładowanie zestawów do kontekstu tylko odbicie](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
> Kontekst tylko odbicia jest nowy w .NET Framework w wersji 2,0.  
  
- Metody takie jak <xref:System.AppDomain.CreateInstance%2A> i <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> klasy mogą ładować zestawy do domeny aplikacji.  
  
- <xref:System.Type.GetType%2A> Metoda <xref:System.Type> klasy może ładować zestawy.  
  
- <xref:System.AppDomain.Load%2A> Metoda <xref:System.AppDomain?displayProperty=nameWithType> klasy może ładować zestawy, ale jest używana głównie do współdziałania z modelem com. Nie należy używać go do ładowania zestawów do domeny aplikacji innej niż domena aplikacji, z której jest wywoływana.  
  
> [!NOTE]
> Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe. Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.  
  
 Można określić sposób udostępniania kodu skompilowanego just-in-Time (JIT) z załadowanych zestawów między domenami aplikacji. Aby uzyskać więcej informacji, zobacz [domeny i zestawy aplikacji](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Przykład  
 Poniższy kod ładuje zestaw o nazwie "example. exe" lub "example. dll" do domeny bieżącej aplikacji, pobiera typ nazwany `Example` z zestawu, pobiera metodę bez parametrów o nazwie `MethodA` dla tego typu i wykonuje metodę. Aby uzyskać pełną dyskusję na temat uzyskiwania informacji z załadowanego zestawu, zobacz [dynamiczne ładowanie i używanie typów](../reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Programowanie przy użyciu domen aplikacji](application-domains.md#programming-with-application-domains)
- [Odbicie](../reflection-and-codedom/reflection.md)
- [Używanie domeny aplikacji](use.md)
- [Porady: ładowanie zestawów do kontekstu Reflection-Only](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Domeny aplikacji i zestawy](application-domains.md#application-domains-and-assemblies)
