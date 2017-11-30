---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33c9bdf3cf055ea005542f8b2471963b16c16122
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keyfile"></a>/keyfile
Określa plik zawierający klucz lub parę kluczy, aby zapewnić silnej nazwy zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagany. Plik, który zawiera klucz. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wstawia klucz publiczny w manifeście zestawu i podpisuje następnie zestawie końcowym z kluczem prywatnym. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).  
  
 Jeśli kompilacji z `/target:module`, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Użyj [/DelaySign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz częściowo podpisanych zestawów.  
  
 Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dla każdy moduł język pośredni firmy Microsoft.  
  
 W przypadku obu `/keyfile` i [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator po raz pierwszy próbuje kontener kluczy. Jeśli który zakończy się powodzeniem, zestaw jest podpisany z informacjami w kontenerze kluczy. Jeśli kompilator nie może znaleźć kontener kluczy, spróbuje określić za pomocą pliku `/keyfile`. Jeśli to się powiedzie, zestaw jest podpisany za pomocą informacji w pliku klucza i informacje o kluczu został zainstalowany w kontenerze kluczy (podobnie jak `sn -i`) tak, aby w następnej kompilacji, kontener kluczy będzie nieprawidłowa.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Zobacz [tworzenie i zestawy Using Strong-Named](https://msdn.microsoft.com/library/xwb8f617) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
>  `/keyfile` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy plik źródłowy `Input.vb` i określa plik klucza.  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy i Globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
