---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408578"
---
# <a name="-keyfile"></a>-keyfile
Określa plik zawierający parę klucz lub klucz, aby nadać zestawowi silną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Wymagany. Plik, który zawiera klucz. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wstawia klucz publiczny do manifestu zestawu, a następnie podpisuje końcowy zestaw kluczem prywatnym. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 W przypadku kompilowania za pomocą `-target:module` programu nazwa pliku klucza jest przechowywana w module i włączana do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](addmodule.md).  
  
 Możesz również przekazać informacje o szyfrowaniu do kompilatora z [kontenerem](keycontainer.md). Użyj [-delaysign](delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.  
  
 Można również określić tę opcję jako atrybut niestandardowy ( <xref:System.Reflection.AssemblyKeyFileAttribute> ) w kodzie źródłowym dowolnego modułu języka pośredniego firmy Microsoft.  
  
 W przypadku określenia obu typów `-keyfile` i [--kontenera](keycontainer.md) (za pomocą opcji wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji kompilator próbuje najpierw kontener kluczy. Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji z kontenera kluczy. Jeśli kompilator nie odnajdzie kontenera kluczy, próbuje plik określony z `-keyfile` . Jeśli to się powiedzie, zestaw zostanie podpisany przy użyciu informacji w pliku klucza, a informacje o kluczu są instalowane w kontenerze kluczy (podobnie jak w przypadku `sn -i` ), więc w następnej kompilacji kontener kluczy będzie prawidłowy.  
  
 Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.  
  
 Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../standard/assembly/create-use-strong-named.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
> `-keyfile`Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.

## <a name="example"></a>Przykład

Poniższy kod kompiluje plik źródłowy `Input.vb` i określa plik klucza.

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-Reference (Visual Basic)](reference.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
