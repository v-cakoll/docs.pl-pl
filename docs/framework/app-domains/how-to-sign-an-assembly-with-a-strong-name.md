---
title: 'Instrukcje: Podpisywanie zestawu silną nazwą'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927932"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Instrukcje: Podpisywanie zestawu silną nazwą
Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:  
  
- Za pomocą karty podpisywanie w oknie dialogowym **Właściwości** projektu w programie Visual Studio. Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.  
  
- Za pomocą [konsolidatora zestawu (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) do łączenia modułu kodu .NET Framework (plik. module) z plikiem klucza.  
  
- Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu. Możesz użyć <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> albo atrybutu, w zależności od tego, gdzie znajduje się plik klucza, który ma być używany.  
  
- Przy użyciu opcji kompilatora.  
  
 Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych. Aby uzyskać więcej informacji na temat tworzenia pary kluczy, [zobacz How to: Utwórz parę](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)kluczy publiczny-prywatny.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Aby utworzyć i podpisać zestaw za pomocą silnej nazwą przy użyciu programu Visual Studio  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.  
  
2. Wybierz kartę podpisywanie.  
  
3. Zaznacz pole **podpisz zestaw** .  
  
4. W polu **Wybierz plik klucza o silnej nazwie** wybierz  **\<Przeglądaj... >** , a następnie przejdź do pliku klucza. Aby utworzyć nowy plik klucza, wybierz  **\<pozycję Nowy... >** i wprowadź jej nazwę w oknie dialogowym **Tworzenie klucza silnej nazwy** .  
  
> [!NOTE]
> Aby opóźnić [podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md), wybierz plik klucza publicznego.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Aby utworzyć i podpisać zestaw za pomocą silnej nazwy przy użyciu programu Assembly Linker  
  
- W [wiersz polecenia dla deweloperów dla programu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md)wpisz następujące polecenie:  
  
     **Al** **/out:** \<AssemblyNameModuleName> > **/KeyFile**:filename\< *\<* >  
  
     gdzie:  
  
     *assemblyName*  
     Nazwa zestawu podpisanego za pomocą silnej nazwy (plik dll lub exe), który zostanie wyemitowany przez program Assembly Linker.  
  
     *moduleName*  
     Nazwa modułu kodu programu .NET Framework (plik netmodule) zawierającego co najmniej jeden typ. Można utworzyć plik. module, kompilując kod z `/target:module` przełącznikiem w C# lub Visual Basic.  
  
     *keyfileName*  
     Nazwa kontenera lub pliku zawierającego parę kluczy. Program Assembly Linker interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.  
  
 Poniższy przykład podpisuje zestaw `MyAssembly.dll` silną nazwą przy użyciu pliku `sgKey.snk`klucza.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [konsolidator zestawu](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Aby podpisać zestaw za pomocą silnej nazwy przy użyciu atrybutów  
  
1. Dodaj atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> or do pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
  
2. Skompiluj w normalny sposób plik kodu źródłowego.  
  
> [!NOTE]
> Kompilatory C# i Visual Basic nie generują ostrzeżeń kompilatora (odpowiednio CS1699 i BC41008), gdy napotkają <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> lub w kodzie źródłowym. Można zignorować te ostrzeżenia.  
  
 W poniższym przykładzie jest używany <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut z plikiem klucza o nazwie `keyfile.snk`, który znajduje się w katalogu, w którym skompilowano zestaw.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego. Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Aby podpisać zestaw za pomocą silnej nazwy przy użyciu kompilatora  
  
- Kompiluj plik lub `/keyfile` pliki kodu źródłowego z opcją kompilatora lub `/delaysign` w C# Visual Basic `/KEYFILE` `/DELAYSIGN` lub opcję konsolidatora w. C++ Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza. W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.  
  
     Aby uzyskać informacje o opóźnieniu podpisywania, zobacz [opóźnienie podpisywania zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     W poniższym przykładzie użyto C# kompilatora i podpisuje zestaw `UtilityLibrary.dll` silną nazwą przy użyciu pliku `sgKey.snk`klucza.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Zarządzanie podpisywaniem zestawu i manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
