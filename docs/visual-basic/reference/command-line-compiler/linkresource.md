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
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005487"
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
 Opcjonalny. Nazwa logiczna zasobu. Nazwa, która jest używana do ładowania zasobu. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publiczny, czy prywatny w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`. Domyślnie `filename` jest publiczna w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-linkresource` nie osadza pliku zasobów w pliku wyjściowym; Użyj opcji `-resource`, aby to zrobić.  
  
 Opcja `-linkresource` wymaga jednej z opcji `-target` innej niż `-target:module`.  
  
 Jeśli `filename` to .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w przestrzeni nazw <xref:System.Resources>. (Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć metod, które zaczynają się od `GetManifestResource` w klasie <xref:System.Reflection.Assembly>.  
  
 Nazwa pliku może być dowolnym formatem pliku. Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.  
  
 Krótka forma `-linkresource` jest `-linkres`.  
  
> [!NOTE]
> Opcja `-linkresource` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb` i linki do pliku zasobów `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
