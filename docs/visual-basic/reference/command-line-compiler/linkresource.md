---
title: -linkresource — (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 4f4b3db768b5466f8912b66a0a4709d0f773c1f3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047194"
---
# <a name="-linkresource-visual-basic"></a>-linkresource — (Visual Basic)
Tworzy łącze do zarządzanego zasobem.  
  
## <a name="syntax"></a>Składnia  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagane. Plik zasobów, aby utworzyć łącze do zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").  
  
 `identifier`  
 Opcjonalna. Nazwa logiczna zasobu. Nazwa która jest używana do ładowania zasobów. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publicznych lub prywatnych w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`. Domyślnie `filename` jest publiczna w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 `-linkresource` Opcja nie jest możliwe osadzanie pliku zasobów w pliku wyjściowym; użyj `-resource` opcję, aby to zrobić.  
  
 `-linkresource` Opcja wymaga jednej z `-target` opcji innych niż `-target:module`.  
  
 Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw. (Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Dostęp do wszystkich innych zasobów w czasie wykonywania, użyj metody, które zaczynają się od `GetManifestResource` w <xref:System.Reflection.Assembly> klasy.  
  
 Nazwa pliku może być dowolnym formacie pliku. Na przykład można wprowadzić natywną DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej i dostępne z kodu zarządzanego w zestawie.  
  
 Krótkiej formy `-linkresource` jest `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Opcja nie jest dostępna z poziomu środowiska projektowego programu Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb` i łącza do pliku zasobów `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
