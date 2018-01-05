---
title: /keycontainer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b91025fb44164c03c43a3b5ed7341ab009f352e9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="keycontainer"></a>/keycontainer
Określa nazwę kontenera kluczy parę kluczy zapewnić silnej nazwy zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`container`|Wymagany. Plik kontenera, który zawiera klucz. Nazwę pliku należy ująć w cudzysłów (""), jeśli nazwa zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilator tworzy składnik zabezpieczać przez wstawianie klucza publicznego do manifestu zestawu i podpisywania z kluczem prywatnym zestawie końcowym. Aby wygenerować plik klucza, wpisz `sn -k``file` w wierszu polecenia. `-i` Opcja powoduje zainstalowanie pary kluczy do kontenera. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Jeśli kompilacji z `/target:module`, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute>) w kodzie źródłowym dla każdy moduł język pośredni (MSIL) firmy Microsoft.  
  
 Można również przekazać do kompilatora z informacjami szyfrowania [/KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Użyj [/DelaySign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz częściowo podpisanych zestawów.  
  
 Zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
>  `/keycontainer` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy plik źródłowy `Input.vb` i Określa kontener klucza.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
