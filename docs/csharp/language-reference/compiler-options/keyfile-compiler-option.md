---
title: -keyfile (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970257"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (Opcje kompilatora C#)
Określa nazwę pliku zawierającą klucz kryptograficzny.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|----------|----------------|  
|`file`|Nazwa pliku zawierającego klucz silnej nazwy.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, kompilator wstawia klucz publiczny z określonego pliku do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym. Aby wygenerować plik klucza, `file` wpisz sn -k w wierszu polecenia.  
  
 Jeśli skompilować z **-target:module**, nazwa pliku klucza jest utrzymywana w module i włączone do zestawu, który jest tworzony podczas kompilowania zestawu z [-addmodule](./addmodule-compiler-option.md).  
  
 Można również przekazać informacje szyfrowania do kompilatora z [-keycontainer](./keycontainer-compiler-option.md). Użyj [-delaysign,](./delaysign-compiler-option.md) jeśli chcesz, aby zestaw częściowo podpisany.  
  
 W przypadku, gdy zarówno -keyfile i -keycontainer są określone (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator najpierw spróbuje kontenera kluczy. Jeśli to się powiedzie, zestaw jest podpisany z informacjami w kontenerze kluczy. Jeśli kompilator nie znajdzie kontenera kluczy, spróbuje plik określony z -keyfile. Jeśli to się powiedzie, zestaw jest podpisany z informacjami w pliku klucza, a informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnie jak sn -i), tak aby podczas następnej kompilacji kontener kluczy był prawidłowy.  
  
 Należy zauważyć, że plik klucza może zawierać tylko klucz publiczny.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości Podpisywania.**  
  
3. Zmodyfikuj właściwość **Wybierz właściwość pliku klucza silnej nazwy.**  
  
 Można programowo uzyskać dostęp do <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>tej opcji kompilatora z .  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
