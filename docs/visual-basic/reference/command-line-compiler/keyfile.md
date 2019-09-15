---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 30b890cf3d523d1e33b433a1ff6109759bd9a5e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972326"
---
# <a name="-keyfile"></a>-keyfile
Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagane. Plik, który zawiera klucz. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Jeśli kompilujesz za `-target:module`pomocą, nazwa pliku klucza jest przechowywana w module i wbudowana w zestaw, który jest tworzony podczas kompilowania zestawu za pomocą [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Możesz również przekazać informacje o szyfrowaniu do kompilatora z [kontenerem](../../../visual-basic/reference/command-line-compiler/keycontainer.md). Użyj [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.  
  
 Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dowolnego modułu języka pośredniego firmy Microsoft.  
  
 W przypadku określenia `-keyfile` obu typów i [--kontenera](../../../visual-basic/reference/command-line-compiler/keycontainer.md) (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator próbuje najpierw kontener kluczy. Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy. Jeśli kompilator nie odnajdzie kontenera kluczy, próbuje plik określony z `-keyfile`. Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak `sn -i`w przypadku), więc w następnej kompilacji kontener kluczy będzie prawidłowy.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
> `-keyfile` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje plik `Input.vb` źródłowy i określa plik klucza.  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
