---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 5892baaa2732d95cfe698147e06b914af968adc5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929425"
---
# <a name="-keycontainer"></a>-keycontainer
Określa nazwę kontenera kluczy, aby nadać zestawowi silną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`container`|Wymagany. Plik kontenera, który zawiera klucz. Nazwa pliku powinna być ujęta w cudzysłów (""), jeśli nazwa zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilator tworzy składnik udostępniony, wstawiając klucz publiczny do manifestu zestawu i podpisując końcowy zestaw z kluczem prywatnym. Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia. `-i` Opcja powoduje zainstalowanie pary kluczy w kontenerze. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 W przypadku kompilowania `-target:module`za pomocą programu nazwa pliku klucza jest przechowywana w module i włączana do zestawu, który jest tworzony podczas kompilowania zestawu za pomocą [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Można również określić tę opcję jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyNameAttribute>) w kodzie źródłowym dla dowolnego modułu języka pośredniego (MSIL) firmy Microsoft.  
  
 Możesz również przekazać informacje o szyfrowaniu do kompilatora za pomocą [-KeyFile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Użyj [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , jeśli chcesz użyć częściowo podpisanego zestawu.  
  
 Zobacz [Tworzenie i używanie zestawów o silnych nazwach,](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Aby uzyskać więcej informacji na temat podpisywania zestawu.  
  
> [!NOTE]
> `-keycontainer` Opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje plik `Input.vb` źródłowy i Określa kontener kluczy.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
