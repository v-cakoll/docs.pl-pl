---
title: 'Jak: Podpisywanie zestawu o silnej nazwie'
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
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160316"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Jak: Podpisywanie zestawu o silnej nazwie

> [!NOTE]
> Mimo że program .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie wymaga silnych nazw. Aby uzyskać więcej informacji, zobacz [Silne podpisywanie nazw](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) w usyjanie usługi GitHub.

Istnieje kilka metod podpisywania zestawu za pomocą silnej nazwy:  
  
- Za pomocą **karty Podpisywanie** w oknie dialogowym **Właściwości** projektu w programie Visual Studio. Jest to najprostsza i najwygodniejsza metoda podpisywania zestawów za pomocą silnych nazw.  
  
- Za pomocą [konsolidatora zestawów (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) połączyć moduł kodu .NET Framework (plik *.netmodule)* z plikiem klucza.  
  
- Przy użyciu atrybutów zestawu w celu wstawienia informacji o silnej nazwie do kodu. Można użyć atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> lub atrybutu, w zależności od tego, gdzie znajduje się plik klucza do użycia.  
  
- Przy użyciu opcji kompilatora.  
  
 Aby podpisać zestaw za pomocą silnej nazwy, trzeba mieć parę kluczy kryptograficznych. Aby uzyskać więcej informacji na temat tworzenia pary kluczy, zobacz [Jak: Tworzenie pary kluczy publiczno-prywatnych](create-public-private-key-pair.md).  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Tworzenie i podpisywanie zestawu o silnej nazwie przy użyciu programu Visual Studio  
  
1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.  
  
2. Wybierz kartę **Podpisywanie.**  
  
3. Wybierz pole **Podpisz złożenie.**  
  
4. W polu **Wybierz silną nazwę pliku klucza** wybierz pozycję **Przeglądaj**, a następnie przejdź do pliku klucza. Aby utworzyć nowy plik klucza, wybierz pozycję **Nowy** i wprowadź jego nazwę w oknie dialogowym **Tworzenie silnego klucza nazwy.**  
  
> [!NOTE]
> Aby [opóźnić podpisanie zestawu,](delay-sign.md)wybierz plik klucza publicznego.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Tworzenie i podpisywanie złożenia o silnej nazwie przy użyciu konsolidatora złożenia  
  
W [wierszu polecenia dewelopera dla programu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)wprowadź następujące polecenie:  

**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*>  

Gdzie:  

- *AssemblyName* to nazwa zestawu silnie podpisanego *(pliku dll* lub *pliku exe),* który będzie emitować łącze zestawu.  
  
- *moduleName* to nazwa modułu kodu .NET Framework (pliku *.netmodule),* który zawiera jeden lub więcej typów. Plik *.netmodule* można utworzyć, kompilując `/target:module` kod za pomocą przełącznika w języku C# lub Visual Basic.
  
- *keyfileName* to nazwa kontenera lub pliku zawierającego parę kluczy. Konsolidator zestawów interpretuje ścieżkę względną w stosunku do bieżącego katalogu.  

Poniższy przykład podpisuje zestaw *MyAssembly.dll* o silnej nazwie przy użyciu pliku *klucza sgKey.snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [Łączenie złożenia](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Podpisywanie zestawu o silnej nazwie przy użyciu atrybutów  
  
1. Dodaj <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> lub <xref:System.Reflection.AssemblyKeyNameAttribute> atrybut do pliku kodu źródłowego i określ nazwę pliku lub kontenera, który zawiera parę kluczy do użycia podczas podpisywania zestawu o silnej nazwie.  

2. Skompiluj w normalny sposób plik kodu źródłowego.  

   > [!NOTE]
   > Kompilatory Języka C# i Visual Basic wydają ostrzeżenia kompilatora (odpowiednio CS1699 <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> i BC41008), gdy napotkają lub atrybut w kodzie źródłowym. Można zignorować te ostrzeżenia.  

W poniższym <xref:System.Reflection.AssemblyKeyFileAttribute> przykładzie użyto atrybutu z plikiem klucza o nazwie *keyfile.snk*, który znajduje się w katalogu, w którym zestaw jest skompilowany.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Można również opóźnić podpisywanie zestawu podczas kompilowania pliku źródłowego. Aby uzyskać więcej informacji, zobacz [Opóźnienie-sign zestawu](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Podpisywanie zestawu o silnej nazwie przy użyciu kompilatora  

Skompiluj plik kodu `/keyfile` źródłowego lub pliki z opcją `/delaysign` lub `/KEYFILE` `/DELAYSIGN` kompilatorem w językach C# i Visual Basic lub opcją lub konsolidatorem w języku C++. Po nazwie opcji dodaj średnik, a następnie nazwę pliku klucza. W przypadku używania kompilatorów wiersza polecenia można skopiować plik klucza do katalogu, który zawiera pliki kodu źródłowego.  

Aby uzyskać informacje na temat podpisywania opóźnienia, zobacz [Opóźnienie-sign zestawu](delay-sign.md).  

W poniższym przykładzie użyto kompilatora C# i podpisuje zestaw *UtilityLibrary.dll* o silnej nazwie przy użyciu pliku *klucza sgKey.snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
- [Jak: Tworzenie pary kluczy publiczno-prywatnych](create-public-private-key-pair.md)
- [Al.exe (konsolidator zestawów)](../../framework/tools/al-exe-assembly-linker.md)
- [Podpisywanie zestawu z opóźnieniem](delay-sign.md)
- [Zarządzanie podpisywaniem zestawu i manifestu](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
