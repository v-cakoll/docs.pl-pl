---
title: -keyfile (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d120b325f433108cd1b01dd1c25d2a0e55da401b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keyfile-c-compiler-options"></a>/keyfile (opcje kompilatora C#)
Określa nazwę pliku zawierającego klucz kryptograficzny.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|----------|----------------|  
|`file`|Nazwa pliku zawierającego klucz silnej nazwy.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, kompilator wstawia klucza publicznego z określonego pliku do manifestu zestawu i podpisuje następnie zestawie końcowym z kluczem prywatnym. Aby wygenerować plik klucza, wpisz sn -k `file` w wierszu polecenia.  
  
 Jeśli kompilacji z **/target: module**, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [/KeyContainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Użyj [/DelaySign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Jeśli chcesz częściowo podpisanych zestawów.  
  
 W przypadku/KeyFile określony zarówno i/KeyContainer (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator próbują używać najpierw kontener kluczy. Jeśli który zakończy się powodzeniem, zestaw jest podpisany z informacjami w kontenerze kluczy. Kompilator nie może znaleźć kontener kluczy, spróbuje plik określony z/KeyFile. Jeśli który zakończy się powodzeniem, zestaw jest podpisany za pomocą informacji w pliku klucza i informacje o kluczu zostaną zainstalowane w kontenerze kluczy (podobnie jak sn -i), aby w następnej kompilacji, kontener kluczy będzie nieprawidłowa.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu.  
  
2.  Kliknij przycisk **podpisywanie** strony właściwości.  
  
3.  Modyfikowanie **wybierz plik klucza o silnej nazwie** właściwości.  
  
 Programowo dostęp do tej opcji kompilatora z <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
