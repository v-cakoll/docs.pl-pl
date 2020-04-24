---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335481"
---
# <a name="-linkresource-visual-basic"></a>-linkresource — (Visual Basic)
Tworzy łącze do zarządzanego zasobu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

lub  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagany. Plik zasobu, który ma zostać połączony z zestawem. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").  
  
 `identifier`  
 Element opcjonalny. Nazwa logiczna zasobu. Nazwa, która jest używana do ładowania zasobu. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publiczny, czy prywatny w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`. Domyślnie `filename` jest on publiczny w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 `-linkresource` Opcja nie osadza pliku zasobów w pliku wyjściowym; Użyj opcji `-resource` , aby to zrobić.  
  
 `-linkresource` Opcja wymaga jednej z `-target` opcji innych niż `-target:module`.  
  
 Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw. (Aby uzyskać więcej informacji, <xref:System.Resources.ResourceManager>Zobacz.) Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć metod, `GetManifestResource` które zaczynają się od <xref:System.Reflection.Assembly> klasy.  
  
 Nazwa pliku może być dowolnym formatem pliku. Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.  
  
 Krótka forma `-linkresource` to `-linkres`.  
  
> [!NOTE]
> Ta `-linkresource` opcja jest niedostępna w środowisku programistycznym programu Visual Studio; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb` i łączy się z plikiem `rf.resource`zasobów.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
