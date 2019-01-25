---
title: -keyfile (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bd89a5fa58507528b2a70efde04ecd2a6f601b39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605607"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (opcje kompilatora C#)
Określa nazwę pliku zawierającego klucz kryptograficzny.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|----------|----------------|  
|`file`|Nazwa pliku zawierającego klucz silnej nazwy.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, kompilator wstawia klucz publiczny z określonego pliku do manifestu zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby wygenerować plik klucza, wpisz sn -k `file` w wierszu polecenia.  
  
 Jeśli kompilujesz z opcją **-target: module**, nazwę pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Można również przekazać szyfrowania informacji do kompilatora przy użyciu [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Użyj [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli chcesz, aby częściowo podpisany zestawu.  
  
 W przypadku, gdy - keyfile określony zarówno i - keycontainer (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator spróbuje najpierw kontenera kluczy. Jeśli się to powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy. Jeśli kompilator nie znajdzie kontenera kluczy, spróbuje pliku określonego przez - keyfile. Jeśli się to powiedzie, zestaw zostanie podpisany przy użyciu informacji z pliku klucza, a informacje o kluczu zostanie zainstalowany w kontenerze kluczy (podobnie jak sn -i), aby przy następnej kompilacji będzie obowiązywać kontenera kluczy.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Kliknij przycisk **podpisywanie** stronę właściwości.  
  
3.  Modyfikowanie **wybierz plik klucza o silnej nazwie** właściwości.  
  
 Programowego dostępu do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
