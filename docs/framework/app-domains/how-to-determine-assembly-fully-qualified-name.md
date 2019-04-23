---
title: 'Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60a4ef1f5bde121d5773925437307b2749aa7282
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097541"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a>Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu
Aby dowiedzieć się, w pełni kwalifikowana nazwa zestawu w globalnej pamięci podręcznej, użyj Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Zobacz [jak: Wyświetlanie zawartości globalnej pamięci podręcznej](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Dla zestawów, które nie znajdują się w globalnej pamięci podręcznej, można uzyskać w pełni kwalifikowanej nazwy zestawu na kilka sposobów: można użyć kod służący do wypełniania wyjściowego informacji konsoli lub do zmiennej lub można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.  
  
-   Jeśli zestaw jest już załadowany przez aplikację, możesz pobrać wartość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości do pobrania w pełni kwalifikowana nazwa. Czy zestaw znajduje się w pamięci podręcznej GAC, można użyć tej metody. Przykład stanowi ilustrację.  
  
-   Jeśli znasz ścieżka systemu plików zestawu, można wywołać statyczną (`Shared` w języku Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodę, aby uzyskać w pełni kwalifikowanej nazwy zestawu. Poniżej przedstawiono prosty przykład.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Możesz użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zbadać metadanych zestawu, który zawiera w pełni kwalifikowana nazwa.  
  
 Aby uzyskać więcej informacji na temat ustawienia zestawu atrybutów, takich jak wersji, kultury i nazwy zestawu, zobacz [Konfigurowanie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md). Aby uzyskać więcej informacji na temat zapewniając zestawu z silną nazwą, zobacz [tworzenie i zestawy Using Strong-Named](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób wyświetlania w pełni kwalifikowana nazwa zestawu zawierającego określonej klasy do konsoli. Ponieważ pobiera nazwę zestawu, który aplikacji został już załadowany, nie ma znaczenia, czy zestaw znajduje się w pamięci podręcznej GAC.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md)
- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
