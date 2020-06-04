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
ms.openlocfilehash: 43ebb61efa26ed11af573e2c4e73a6fd71ac0902
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403203"
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
 Opcjonalny. Nazwa logiczna zasobu. Nazwa, która jest używana do ładowania zasobu. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy plik jest publiczny, czy prywatny w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public` . Domyślnie jest on `filename` publiczny w zestawie.  
  
## <a name="remarks"></a>Uwagi  
 `-linkresource`Opcja nie osadza pliku zasobów w pliku wyjściowym; Użyj `-resource` opcji, aby to zrobić.  
  
 `-linkresource`Opcja wymaga jednej z `-target` opcji innych niż `-target:module` .  
  
 Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw. (Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager> .) Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć metod, które zaczynają się od `GetManifestResource` <xref:System.Reflection.Assembly> klasy.  
  
 Nazwa pliku może być dowolnym formatem pliku. Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.  
  
 Krótka forma `-linkresource` to `-linkres` .  
  
> [!NOTE]
> Ta `-linkresource` opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb` i łączy się z plikiem zasobów `rf.resource` .  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-Target (Visual Basic)](target.md)
- [-Resource (Visual Basic)](resource.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
