---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 38740ed7ab7904feb2ca95eb70c916fbdbaef71e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654346"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Tworzy łącze do zasobów zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagana. Plik zasobu, aby utworzyć łącze do zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").  
  
 `identifier`  
 Opcjonalna. Nazwa logiczna zasobu. Nazwa, która jest używana do załadowania zasobu. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publicznych lub prywatnych w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`. Domyślnie `filename` jest publiczny w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 `-linkresource` Opcja nie jest możliwe osadzanie pliku zasobów w pliku wyjściowym; użyj `-resource` opcję, aby to zrobić.  
  
 `-linkresource` Opcja wymaga jednego z `-target` opcje inne niż `-target:module`.  
  
 Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw. (Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Aby uzyskać dostęp do innych zasobów w czasie wykonywania, należy użyć metody, które zaczynają się od `GetManifestResource` w <xref:System.Reflection.Assembly> klasy.  
  
 Nazwa pliku może być dowolnym formacie pliku. Na przykład można ustawić natywnej biblioteki DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej zestawów i dostępne z kodu zarządzanego w zestawie.  
  
 Krótka forma z `-linkresource` jest `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Opcja nie jest dostępny w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb` i łącza do pliku zasobów `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
