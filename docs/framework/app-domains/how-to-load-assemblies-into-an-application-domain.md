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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd6f14f89d143edd03f8b5d028ec84315b2f2e97
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268526"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Porady: ładowanie zestawów do domeny aplikacji
Istnieje kilka sposobów, aby załadować zestawu do domeny aplikacji. Zalecaną metodą jest użycie `static` (`Shared` w języku Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metody <xref:System.Reflection.Assembly?displayProperty=nameWithType> klasy. Inne sposoby, które zestawy można załadować obejmują:  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> Metody <xref:System.Reflection.Assembly> klasy ładuje zestaw podanej lokalizacji pliku. Ładowanie zestawów przy użyciu tej metody używa kontekstu różne obciążenia.  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> i <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody ładowania zestawu do kontekstu reflection-only. Zestawy ładowane w tym kontekście można zbadać, ale nie jest to wykonywane, dzięki czemu badania zestawów, przeznaczonych dla innych platform. Zobacz [porady: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Kontekstu reflection-only jest nowa w .NET Framework w wersji 2.0.  
  
-   Metody takie jak <xref:System.AppDomain.CreateInstance%2A> i <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> klasy można ładować zestawy do domeny aplikacji.  
  
-   <xref:System.Type.GetType%2A> Metody <xref:System.Type> klasy można ładować zestawy.  
  
-   <xref:System.AppDomain.Load%2A> Metody <xref:System.AppDomain?displayProperty=nameWithType> klasy można ładować zestawy, ale jest używany głównie dla współdziałania COM. Nie można stosować ładować zestawy do domeny aplikacji innej niż ta, z którego jest wywoływana.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework w wersji 2.0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji programu .NET Framework, który ma wyższy numer wersji niż obecnie załadowanym środowiskiem uruchomieniowym. Dotyczy to kombinacja składniki główny i pomocniczy numer wersji.  
  
 Można określić sposób just-in-time (JIT) skompilowany kod z załadowanych zestawów jest współużytkowane między domenami aplikacji. Aby uzyskać więcej informacji, zobacz [domeny aplikacji i zestawy](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## <a name="example"></a>Przykład  
 Następujące obciążenia kod pobiera zestaw o nazwie "example.exe" lub "example.dll" do bieżącej domeny aplikacji typu o nazwie `Example` z zestawu, pobiera bez parametrów metody o nazwie `MethodA` wpisz i wykonuje metodę. Wyczerpujące omówienie na uzyskiwanie informacji z załadowanego zestawu, zobacz [dynamiczne ładowanie i przy użyciu typów](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [Programowanie z domenami aplikacji](application-domains.md#programming-with-application-domains)  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Używanie domen aplikacji](../../../docs/framework/app-domains/use.md)  
 [Instrukcje: ładowanie zestawów do kontekstu Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [Domeny aplikacji i zestawy](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
