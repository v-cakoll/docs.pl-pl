---
title: 'Instrukcje: Tworzenie pary kluczy publiczny-prywatny'
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122519"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Instrukcje: Tworzenie pary kluczy publiczny-prywatny

Aby podpisać zestaw za pomocą silnej nazwy, musisz mieć parę kluczy publiczny/prywatny. Ta para publicznych i prywatnych kluczy kryptograficznych jest używana podczas kompilacji w celu utworzenia zestawu o silnej nazwie. Parę kluczy można utworzyć za pomocą [Narzędzia silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md). Pliki pary kluczy zazwyczaj mają rozszerzenie *. snk* .

> [!NOTE]
> W programie Visual Studio strony C# właściwości projektu i Visual Basic zawierają kartę **podpisywanie** , która umożliwia wybieranie istniejących plików kluczy lub generowanie nowych plików kluczy bez korzystania z *SN. exe*. W C++wizualizacji, możesz określić lokalizację istniejącego pliku klucza na stronie właściwości **Zaawansowane** w sekcji **konsolidator** w sekcji **Właściwości konfiguracji** w oknie **strony właściwości** . Użycie atrybutu <xref:System.Reflection.AssemblyKeyFileAttribute> do identyfikowania par plików kluczy było przestarzałe, począwszy od programu Visual Studio 2005.

## <a name="create-a-key-pair"></a>Tworzenie pary kluczy

Aby utworzyć parę kluczy, w wierszu polecenia wpisz następujące polecenie:

**SN —** *Nazwa pliku* \<k>

W tym poleceniu *Nazwa pliku* jest nazwą pliku wyjściowego zawierającego parę kluczy.

Poniższy przykład tworzy parę kluczy o nazwie *sgKey. snk*.

```cmd
sn -k sgKey.snk
```

Jeśli zamierzasz opóźnić podpisywanie zestawu i kontrolować całą parę kluczy (najprawdopodobniej poza scenariuszami testowymi), możesz użyć poniższych poleceń, aby wygenerować parę kluczy, a następnie wyodrębnić z niej klucz publiczny do osobnego pliku. Najpierw Utwórz parę kluczy:

```cmd
sn -k keypair.snk
```

Następnie wyodrębnij klucz publiczny z pary kluczy i skopiuj go do oddzielnego pliku:

```cmd
sn -p keypair.snk public.snk
```

Po utworzeniu pary kluczy należy umieścić w niej plik, w którym znajdują się narzędzia podpisywania silnej nazwy.

Podczas podpisywania zestawu o silnej nazwie [konsolidator zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) wyszukuje plik klucza względem bieżącego katalogu i do katalogu wyjściowego. Używając kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.

Jeśli używasz wcześniejszej wersji programu Visual Studio, która nie ma karty **podpisywanie** we właściwościach projektu, zalecana lokalizacja pliku klucza jest katalogiem projektu z atrybutem pliku określonym w następujący sposób:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)
