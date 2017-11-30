---
title: "Porady: podpisywanie zestawu silną nazwą"
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
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: babd0f6a9b1babf02677d6c6c41c664e0a6541b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Porady: podpisywanie zestawu silną nazwą
Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:  
  
-   Za pomocą **podpisywanie** kartę w projekcie **właściwości** okno dialogowe w programie Visual Studio. Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.  
  
-   Za pomocą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) połączyć modułu kodu .NET Framework (plik modułu .netmodule) z pliku klucza.  
  
-   Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu. Możesz użyć dowolnej <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybut, w zależności od tego, gdzie znajduje się plik klucza do użycia.  
  
-   Przy użyciu opcji kompilatora.  
  
 Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych. Aby uzyskać więcej informacji o tworzeniu parę kluczy, zobacz [porady: tworzenie pary kluczy publiczno-prywatnych](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Aby utworzyć i podpisać zestaw za pomocą silnej nazwą przy użyciu programu Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.  
  
2.  Wybierz **podpisywanie** kartę.  
  
3.  Wybierz **Podpisz zestaw** pole.  
  
4.  W **wybierz plik klucza o silnej nazwie** wybierz  **\<Przeglądaj >**, a następnie przejdź do pliku klucza. Aby utworzyć nowy plik klucza, wybierz  **\<nowy... >** i wprowadź jego nazwę w **tworzenie silnej nazwy klucza** okno dialogowe.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Aby utworzyć i podpisać zestaw za pomocą silnej nazwy przy użyciu programu Assembly Linker  
  
-   W [wiersz polecenia programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), wpisz następujące polecenie:  
  
     **Al** **/out:**\<*assemblyName*> *\<Nazwa_modułu >* **/KeyFile:** \<  *keyfileName*>  
  
     gdzie:  
  
     *assemblyName*  
     Nazwa zestawu podpisanego za pomocą silnej nazwy (plik dll lub exe), który zostanie wyemitowany przez program Assembly Linker.  
  
     *Nazwa modułu*  
     Nazwa modułu kodu programu .NET Framework (plik netmodule) zawierającego co najmniej jeden typ. Utwórz plik modułu .netmodule, kompilacja kodu za pomocą `/target:module` przełącznika w języku C# lub Visual Basic.  
  
     *keyfileName*  
     Nazwa kontenera lub pliku zawierającego parę kluczy. Program Assembly Linker interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.  
  
 Poniższy przykład podpisuje zestawu `MyAssembly.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Aby uzyskać więcej informacji o tym narzędziu, zobacz [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Aby podpisać zestaw za pomocą silnej nazwy przy użyciu atrybutów  
  
1.  Dodaj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera pary kluczy do użycia podczas podpisywania zestawu o silnej nazwie.  
  
2.  Skompiluj w normalny sposób plik kodu źródłowego.  
  
> [!NOTE]
>  Kompilatory języka C# i Visual Basic wystawiać ostrzeżeń kompilatora (CS1699 i BC41008, odpowiednio) Jeśli wystąpi <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu w kodzie źródłowym. Można zignorować te ostrzeżenia.  
  
 W poniższym przykładzie użyto <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut z pliku klucza o nazwie `keyfile.snk`, który znajduje się w katalogu, w którym ma być kompilowana zestawu.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego. Aby uzyskać więcej informacji, zobacz [opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Aby podpisać zestaw za pomocą silnej nazwy przy użyciu kompilatora  
  
-   Kompiluj z pliku kodu źródłowego lub pliki z `/keyfile` lub `/delaysign` — opcja kompilatora C# i Visual Basic lub `/KEYFILE` lub `/DELAYSIGN` — opcja konsolidatora w języku C++. Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza. W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.  
  
     Aby uzyskać informacje na podpisywanie opóźnione, zobacz [opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     Poniższy przykład używa kompilatora C# i podpisuje zestawu `UtilityLibrary.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Porady: tworzenie pary kluczy publiczno prywatnych](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Zarządzanie zestawem i podpisywanie manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [Strona podpisywania, Projektant projektu](https://msdn.microsoft.com/library/0k50fs3b)
