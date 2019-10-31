---
title: 'Instrukcje: podpisywanie zestawu za pomocą silnej nazwy'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: c9ddbcf8f7b6307ab2d89b819aee4809f753a0fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138611"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Instrukcje: podpisywanie zestawu za pomocą silnej nazwy

> [!NOTE]
> Chociaż platforma .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie potrzebuje silnych nazw. Aby uzyskać więcej informacji, zobacz [Logowanie silnej nazwy](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) w serwisie GitHub.

Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:  
  
- Za pomocą karty **podpisywanie** w oknie dialogowym **Właściwości** projektu w programie Visual Studio. Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.  
  
- Za pomocą [konsolidatora zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) do łączenia modułu kodu .NET Framework (plik *. module* ) z plikiem klucza.  
  
- Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu. Można użyć <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybutu, w zależności od tego, gdzie znajduje się plik klucza do użycia.  
  
- Przy użyciu opcji kompilatora.  
  
 Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych. Aby uzyskać więcej informacji na temat tworzenia pary kluczy, zobacz [How to: Create a Public-Private Key para](create-public-private-key-pair.md).  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Tworzenie i podpisywanie zestawu za pomocą silnej nazwy przy użyciu programu Visual Studio  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.  
  
2. Wybierz kartę **podpisywanie** .  
  
3. Zaznacz pole **podpisz zestaw** .  
  
4. W polu **Wybierz plik klucza o silnej nazwie** wybierz **Przeglądaj**, a następnie przejdź do pliku klucza. Aby utworzyć nowy plik klucza, wybierz pozycję **Nowy** i wprowadź jego nazwę w oknie dialogowym **Tworzenie klucza silnej nazwy** .  
  
> [!NOTE]
> Aby [opóźnić podpisywanie zestawu](delay-sign.md), wybierz plik klucza publicznego.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Tworzenie i podpisywanie zestawu za pomocą silnej nazwy przy użyciu konsolidatora zestawu  
  
W [wiersz polecenia dla deweloperów dla programu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)wprowadź następujące polecenie:  

**Al** **/out:** \<*assemblyName*>  *\<ModuleName >* **/keyfile:** \<*pliku*  

Gdzie:  

- *AssemblyName* jest nazwą silnie podpisanego zestawu (plik *. dll* lub *. exe* ), który będzie emitowany przez konsolidator zestawu.  
  
- *ModuleName* jest nazwą modułu kodu .NET Framework (plik *. module* ), który zawiera jeden lub więcej typów. Można utworzyć plik *modułu. module* , kompilując kod przy użyciu przełącznika `/target:module` w C# lub Visual Basic.
  
- *filename* jest nazwą kontenera lub pliku, który zawiera parę kluczy. Konsolidator zestawu interpretuje ścieżkę względną w odniesieniu do bieżącego katalogu.  

Poniższy przykład podpisuje zestaw plik *. dll* z silną nazwą przy użyciu pliku klucza *sgKey. snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [konsolidator zestawu](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podpisz zestaw silną nazwą przy użyciu atrybutów  
  
1. Dodaj atrybut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> do pliku kodu źródłowego i określ nazwę pliku lub kontenera zawierającego parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie.  
   
2. Skompiluj w normalny sposób plik kodu źródłowego.  
   
   > [!NOTE]
   > Kompilatory C# i Visual Basic generują ostrzeżenia kompilatora (odpowiednio CS1699 i BC41008), gdy napotkają atrybut <xref:System.Reflection.AssemblyKeyFileAttribute> lub <xref:System.Reflection.AssemblyKeyNameAttribute> w kodzie źródłowym. Można zignorować te ostrzeżenia.  

W poniższym przykładzie używany jest atrybut <xref:System.Reflection.AssemblyKeyFileAttribute> z plikiem klucza o nazwie *keyfile. snk*, który znajduje się w katalogu, w którym jest kompilowany zestaw.  

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

Skompiluj plik lub pliki kodu źródłowego przy użyciu opcji kompilatora `/keyfile` lub `/delaysign` w C# i Visual Basic lub opcji konsolidator `/KEYFILE` lub `/DELAYSIGN`. C++ Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza. W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.  

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
