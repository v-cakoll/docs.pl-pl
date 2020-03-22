---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266745"
---
# <a name="-keyfile"></a>-keyfile
Określa plik zawierający klucz lub parę kluczy, aby nadać zestawowi silną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagany. Plik zawierający klucz. Jeśli nazwa pliku zawiera spację, należy ją ująć w cudzysłów (" ").  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw za pomocą klucza prywatnego. Aby wygenerować `sn -k file` plik klucza, wpisz wiersz polecenia. Aby uzyskać więcej informacji, zobacz [Sn.exe (Narzędzie Silnej nazwy).](../../../framework/tools/sn-exe-strong-name-tool.md)  
  
 Jeśli kompilujesz `-target:module`z , nazwa pliku klucza jest utrzymywana w module i włączona do zestawu, który jest tworzony podczas kompilowania zestawu z [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Informacje o szyfrowaniu można również przekazać do kompilatora za pomocą [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Użyj [-delaysign,](../../../visual-basic/reference/command-line-compiler/delaysign.md) jeśli chcesz częściowo podpisanyzesśmy.  
  
 Można również określić tę opcję jako<xref:System.Reflection.AssemblyKeyFileAttribute>atrybut niestandardowy ( ) w kodzie źródłowym dla dowolnego modułu języka pośredniego firmy Microsoft.  
  
 W przypadku, gdy zarówno `-keyfile` i [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) są określone (przez opcję wiersza polecenia lub atrybutu niestandardowego) w tej samej kompilacji, kompilator najpierw próbuje kontenera klucza. Jeśli to się powiedzie, zestaw jest podpisany z informacjami w kontenerze kluczy. Jeśli kompilator nie znajdzie kontenera kluczy, `-keyfile`próbuje plik określony za pomocą pliku . Jeśli to się powiedzie, zestaw jest podpisany z informacjami w pliku klucza, a `sn -i`informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak), tak aby w następnej kompilacji kontener kluczy był prawidłowy.  
  
 Należy zauważyć, że plik klucza może zawierać tylko klucz publiczny.  
  
 Zobacz [Tworzenie i używanie zestawów o silnych nazwach, aby](../../../standard/assembly/create-use-strong-named.md) uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
> Opcja `-keyfile` nie jest dostępna z poziomu środowiska programistycznego programu Visual Studio; jest on dostępny tylko podczas kompilowania z wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy kod kompiluje plik `Input.vb` źródłowy i określa plik klucza.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Visual Basic Kompilator wiersza polecenia](../../../visual-basic/reference/command-line-compiler/index.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
