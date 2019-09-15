---
title: 'Instrukcje: Podpisz zestaw silną nazwą'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973062"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Instrukcje: Podpisz zestaw silną nazwą

> [!NOTE]
> Chociaż platforma .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie potrzebuje silnych nazw. Aby uzyskać więcej informacji, zobacz [Logowanie silnej nazwy](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) w serwisie GitHub.

Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:  
  
- Za pomocą karty **podpisywanie** w oknie dialogowym **Właściwości** projektu w programie Visual Studio. Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.  
  
- Za pomocą [konsolidatora zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) do łączenia modułu kodu .NET Framework (plik *. module* ) z plikiem klucza.  
  
- Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu. Możesz użyć <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> albo atrybutu, w zależności od tego, gdzie znajduje się plik klucza, który ma być używany.  
  
- Przy użyciu opcji kompilatora.  
  
 Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych. Aby uzyskać więcej informacji na temat tworzenia pary kluczy, [zobacz How to: Utwórz parę](create-public-private-key-pair.md)kluczy publiczny-prywatny.  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Tworzenie i podpisywanie zestawu za pomocą silnej nazwy przy użyciu programu Visual Studio  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.  
  
2. Wybierz kartę **podpisywanie** .  
  
3. Zaznacz pole **podpisz zestaw** .  
  
4. W polu **Wybierz plik klucza o silnej nazwie** wybierz **Przeglądaj**, a następnie przejdź do pliku klucza. Aby utworzyć nowy plik klucza, wybierz pozycję **Nowy** i wprowadź jego nazwę w oknie dialogowym **Tworzenie klucza silnej nazwy** .  
  
> [!NOTE]
> Aby [opóźnić podpisywanie zestawu](delay-sign.md), wybierz plik klucza publicznego.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Tworzenie i podpisywanie zestawu za pomocą silnej nazwy przy użyciu konsolidatora zestawu  
  
W [wiersz polecenia dla deweloperów dla programu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)wprowadź następujące polecenie:  

**Al** **/out:** \<AssemblyNameModuleName>/keyfile:filename>  *\<* \<>  

Gdzie:  

- *AssemblyName* jest nazwą silnie podpisanego zestawu (plik *. dll* lub *. exe* ), który będzie emitowany przez konsolidator zestawu.  
  
- *ModuleName* jest nazwą modułu kodu .NET Framework (plik *. module* ), który zawiera jeden lub więcej typów. Można utworzyć plik *. module* , kompilując kod z `/target:module` przełącznikiem w C# lub Visual Basic.
  
- *filename* jest nazwą kontenera lub pliku, który zawiera parę kluczy. Konsolidator zestawu interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.  

Poniższy przykład podpisuje zestaw plik *. dll* z silną nazwą przy użyciu pliku klucza *sgKey. snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [konsolidator zestawu](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podpisz zestaw silną nazwą przy użyciu atrybutów  
  
1. Dodaj atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> or do pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie. <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType>  
   
2. Skompiluj w normalny sposób plik kodu źródłowego.  
   
   > [!NOTE]
   > Kompilatory C# i Visual Basic nie generują ostrzeżeń kompilatora (odpowiednio CS1699 i BC41008), gdy napotkają <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut <xref:System.Reflection.AssemblyKeyNameAttribute> lub w kodzie źródłowym. Można zignorować te ostrzeżenia.  

W poniższym przykładzie używany <xref:System.Reflection.AssemblyKeyFileAttribute> jest atrybut z plikiem klucza o nazwie *keyfile. snk*, który znajduje się w katalogu, w którym jest kompilowany zestaw.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego. Aby uzyskać więcej informacji, zobacz [Opóźnij podpisanie zestawu](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podpisywanie zestawu za pomocą silnej nazwy przy użyciu kompilatora  

Kompiluj plik lub `/keyfile` pliki kodu źródłowego z opcją kompilatora lub `/delaysign` w C# Visual Basic `/KEYFILE` `/DELAYSIGN` lub opcję konsolidatora w. C++ Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza. W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.  

Aby uzyskać informacje dotyczące podpisywania opóźnień, zobacz [Opóźnij podpisanie zestawu](delay-sign.md).  

W poniższym przykładzie użyto C# kompilatora i podpisuje zestaw *UtilityLibrary. dll* silną nazwą przy użyciu pliku klucza *sgKey. snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](create-public-private-key-pair.md)
- [Al.exe (konsolidator zestawów)](../../framework/tools/al-exe-assembly-linker.md)
- [Opóźnij podpisanie zestawu](delay-sign.md)
- [Zarządzanie podpisywaniem zestawu i manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
