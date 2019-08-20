---
title: -keyfile (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: eef843c87b8f1993c3419b261894a6df31096294
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606890"
---
# <a name="-keyfile-c-compiler-options"></a>-keyfile (C# opcje kompilatora)
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
 Gdy ta opcja jest używana, kompilator wstawia klucz publiczny z określonego pliku do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym. Aby wygenerować plik klucza, wpisz SN-k `file` w wierszu polecenia.  
  
 W przypadku kompilowania z **modułem-target:** nazwa pliku klucza jest przechowywana w module i wbudowana w zestaw, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](./addmodule-compiler-option.md).  
  
 Możesz również przekazać informacje o szyfrowaniu do kompilatora z kontenerem [](./keycontainer-compiler-option.md). Użyj [-delaysign](./delaysign-compiler-option.md) , jeśli chcesz użyć częściowo podpisanego zestawu.  
  
 W przypadku określenia zarówno parametru-KeyFile, jak i-containerer (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator najpierw spróbuje kontener kluczy. Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy. Jeśli kompilator nie odnajdzie kontenera kluczy, podejmie próbę pliku określonego za pomocą parametru-keyfile. Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnym do SN-i), tak aby w następnej kompilacji kontener kluczy będzie prawidłowy.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) oraz [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** dla projektu.  
  
2. Kliknij stronę właściwości podpisywanie.  
  
3. Zmodyfikuj właściwość **pliku klucza o silnej nazwie** .  
  
 Można programowo uzyskać dostęp do tej opcji kompilatora <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>przy użyciu.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
