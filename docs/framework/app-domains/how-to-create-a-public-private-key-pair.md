---
title: 'Porady: tworzenie pary kluczy publiczno prywatnych'
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
ms.openlocfilehash: fe799e15655d4ae1d9d9b7303728b503a5e45082
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-a-public-private-key-pair"></a>Porady: tworzenie pary kluczy publiczno prywatnych
Aby podpisać zestaw o silnej nazwie, musi mieć pary kluczy publiczny/prywatny. Ta publicznego i prywatnego klucza kryptograficznego jest używany podczas kompilacji można utworzyć zestawu z silną nazwą. Można utworzyć przy użyciu pary kluczy [narzędzie Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Pliki par kluczy mają zwykle rozszerzenie .snk —.  
  
> [!NOTE]
>  W programie Visual Studio, stron właściwości projektów C# i Visual Basic obejmują **podpisywanie** kartę, która pozwala wybrać istniejące pliki klucza lub do generowania nowych kluczy plików bez użycia Sn.exe. W programie Visual C++, można określić lokalizacji istniejącego pliku klucza w **zaawansowane** stronę właściwości w **konsolidatora** sekcji **właściwości konfiguracji** sekcji **Strony właściwości** okna. Korzystanie z <xref:System.Reflection.AssemblyKeyFileAttribute> atrybut do identyfikowania par kluczy plików wprowadzono przestarzałe, począwszy od [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
### <a name="to-create-a-key-pair"></a>Aby utworzyć pary kluczy  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     **SN — k** \< *nazwy pliku*>  
  
     W tym poleceniu *nazwę pliku* to nazwa pliku wynikowego, zawierającego pary kluczy.  
  
 Poniższy przykład tworzy parę kluczy o nazwie `sgKey.snk`.  
  
```  
sn -k sgKey.snk  
```  
  
 Jeśli zamierzasz opóźnienie Podpisz zestaw i kontrolować pary całego kluczy (która jest mało prawdopodobne poza scenariuszy testowania), można użyć następującego polecenia można wygenerować pary kluczy, a następnie wyodrębnić klucza publicznego z niego w osobnym pliku. Najpierw należy utworzyć pary kluczy:  
  
```  
sn -k keypair.snk  
```  
  
 Następnie wyodrębnić klucza publicznego z pary kluczy i skopiuj go do osobnego pliku:  
  
```  
sn -p keypair.snk public.snk  
```  
  
 Po utworzeniu parę kluczy, możesz umieścić plik, gdzie silna nazwa narzędzia podpisywania można go znaleźć.  
  
 Gdy podpisywanie zestawu silną nazwą [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) szuka klucz pliku względne do bieżącego katalogu i do katalogu wyjściowego. Korzystając z kompilatory w wierszu polecenia, można po prostu skopiuj klucz do bieżącego katalogu zawierającego moduły kodu.  
  
 Jeśli używasz starszej wersji programu Visual Studio, która nie ma **podpisywanie** karcie we właściwościach projektu lokalizacji pliku klucza zalecane jest katalogu projektu z atrybutem pliku określona w następujący sposób:  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
