---
title: "Porady: ustalić zestawu &#39; s w pełni kwalifikowana nazwa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 841bec105f171f3450bfc33ee9052ddb85814a5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>Porady: ustalić zestawu &#39; s w pełni kwalifikowana nazwa
Aby dowiedzieć się, w pełni kwalifikowanej nazwy zestawu w globalnej pamięci podręcznej zestawów, użyj narzędzie globalnej pamięci podręcznej zestawów ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Zobacz [porady: wyświetlanie zawartości globalnej pamięci podręcznej zestawów](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Nazwy zestawu w pełni kwalifikowaną dla zestawów, które nie znajdują się w globalnej pamięci podręcznej zestawów, można uzyskać na kilka sposobów: można użyć kodu do danych wyjściowych informacji w konsoli lub do zmiennej lub skorzystać z [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.  
  
-   Jeśli zestaw jest już załadowany przez aplikację, możesz pobrać wartość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości można uzyskać w pełni kwalifikowanej nazwy. Można użyć tej metody, czy zestaw jest w pamięci GAC. Przykład stanowi ilustrację.  
  
-   Jeśli znasz ścieżki systemu plików zestawu, należy wywołać statycznych (`Shared` w języku Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metody można pobrać nazwy zestawu w pełni kwalifikowana. Poniżej przedstawiono prosty przykład.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.  
  
 Aby uzyskać więcej informacji na temat ustawienia zestawu atrybutów, takich jak wersji, kultury i nazwy zestawu, zobacz [ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md). Aby uzyskać więcej informacji na temat nadanie silnej nazwy zestawu, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób wyświetlania w pełni kwalifikowana nazwa zestawu zawierającego klasę określonej w konsoli. Ponieważ pobiera on nazwę zestawu, który aplikacji został już załadowany, nie ma znaczenia, czy zestaw jest w pamięci GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md)  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
