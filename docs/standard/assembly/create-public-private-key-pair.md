---
title: 'Jak: Tworzenie pary kluczy publiczno-prywatnych'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122519"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Jak: Tworzenie pary kluczy publiczno-prywatnych

Aby podpisać zestaw o silnej nazwie, musisz mieć parę kluczy publicznych/prywatnych. Ta publiczna i prywatna para kluczy kryptograficznych jest używana podczas kompilacji do tworzenia zestawu o silnej nazwie. Parę kluczy można utworzyć za pomocą [narzędzia Silna nazwa (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md). Pliki pary kluczy mają zwykle rozszerzenie *.snk.*

> [!NOTE]
> W programie Visual Studio strony właściwości projektu Języka C# i Visual Basic zawierają kartę **Podpisywanie,** która umożliwia wybranie istniejących plików kluczy lub wygenerowanie nowych plików kluczy bez użycia *programu Sn.exe.* W programie Visual C++ można określić lokalizację istniejącego pliku klucza na stronie **właściwości Zaawansowane** w sekcji **Właściwości** **konfiguracji** w oknie **Strony właściwości.** Użycie atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> do identyfikowania par plików kluczy stało się przestarzałe począwszy od programu Visual Studio 2005.

## <a name="create-a-key-pair"></a>Tworzenie pary kluczy

Aby utworzyć parę kluczy, w wierszu polecenia wpisz następujące polecenie:

*nazwa pliku* **sn –k** \<>

W tym poleceniu *nazwa pliku* jest nazwą pliku wyjściowego zawierającego parę kluczy.

Poniższy przykład tworzy parę kluczy o nazwie *sgKey.snk*.

```cmd
sn -k sgKey.snk
```

Jeśli zamierzasz opóźnić podpisanie zestawu i kontrolować całą parę kluczy (co jest mało prawdopodobne, scenariusze testów zewnętrznych), można użyć następujących poleceń do wygenerowania pary kluczy, a następnie wyodrębnić klucz publiczny z niego do oddzielnego pliku. Najpierw utwórz parę kluczy:

```cmd
sn -k keypair.snk
```

Następnie wyodrębnij klucz publiczny z pary kluczy i skopiuj go do oddzielnego pliku:

```cmd
sn -p keypair.snk public.snk
```

Po utworzeniu pary kluczy należy umieścić plik, w którym można go znaleźć narzędzia do podpisywania silnej nazwy.

Podczas podpisywania zestawu o silnej nazwie [konsolidator zestawu (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) wyszbędzie plik klucza względem bieżącego katalogu i katalogu wyjściowego. Korzystając z kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.

Jeśli używasz starszej wersji programu Visual Studio, która nie ma karty **Podpisywanie** we właściwościach projektu, zalecaną lokalizacją pliku klucza jest katalog projektu z atrybutem pliku określonym w następujący sposób:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
