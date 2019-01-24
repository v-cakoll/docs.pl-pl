---
title: 'Instrukcje: Tworzenie pary kluczy publiczny prywatny'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce346bfe0c20e94673009adb0134fbaab62cf551
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653921"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Instrukcje: Tworzenie pary kluczy publiczny prywatny

Aby podpisać zestaw silną nazwą, musisz mieć parę kluczy publiczny/prywatny. Ta publicznych i prywatnych z pary kluczy kryptograficznych jest używany podczas kompilacji do tworzenia zestawu z silną nazwą. Możesz utworzyć parę kluczy, używając [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Pliki par kluczy mają zwykle rozszerzenie .snk.

> [!NOTE]
> W programie Visual Studio obejmują strony właściwości projektu C# i Visual Basic **podpisywanie** kartę, która pozwala wybrać istniejące pliki klucza lub do generowania nowych kluczy plików bez użycia Sn.exe. W programie Visual C++, należy określić lokalizację istniejącego pliku klucza w **zaawansowane** — strona właściwości w **konsolidatora** części **właściwości konfiguracji** sekcji **Stron właściwości** okna. Korzystanie z <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut do identyfikowania pary pliku klucza stało się przestarzałe, począwszy od programu Visual Studio 2005.

## <a name="to-create-a-key-pair"></a>Aby utworzyć parę kluczy

1.  W wierszu polecenia wpisz następujące polecenie:

     **numery seryjne – k** \< *nazwy pliku*>

     W tym poleceniu *nazwy pliku* to nazwa pliku wyjściowego zawierającego parę kluczy.

 Poniższy przykład tworzy parę kluczy o nazwie `sgKey.snk`.

```
sn -k sgKey.snk
```

 Jeśli zamierzasz opóźnienie Podpisz zestaw i kontrolować pary zupełnie kluczy, (która jest mało prawdopodobne, poza scenariuszy testowania), należy użyć następującego polecenia do wygeneruj parę kluczy, a następnie wyodrębnić klucza publicznego z niego w osobnym pliku. Najpierw Utwórz parę kluczy:

```
sn -k keypair.snk
```

 Następnie Wyodrębnij klucz publiczny z pary kluczy i skopiuj go do osobnego pliku:

```
sn -p keypair.snk public.snk
```

 Po utworzeniu parę kluczy, należy umieścić plik, gdzie podpisywania narzędzia silnymi nazwami mogła go odnaleźć.

 Przy podpisywaniu zestawu silną nazwą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) szuka klucza pliku względną do bieżącego katalogu i do katalogu wyjściowego. Korzystając z kompilatorów wiersza polecenia, można po prostu skopiować klucz do bieżącego katalogu zawierającego moduły kodu.

 Jeśli używasz starszej wersji programu Visual Studio, który nie ma **podpisywanie** karcie we właściwościach projektu lokalizacji pliku klucza zalecane jest katalogu projektu za pomocą atrybutu pliku określona w następujący sposób:

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a>Zobacz także

- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
