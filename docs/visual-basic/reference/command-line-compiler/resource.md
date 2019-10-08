---
title: -Resource (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005193"
---
# <a name="-resource-visual-basic"></a>-Resource (Visual Basic)
Osadza zasób zarządzany w zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

lub  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Wymagany. Nazwa pliku zasobu do osadzenia w pliku wyjściowym. Domyślnie `filename` jest publiczna w zestawie. Nazwa pliku należy ująć w cudzysłów (""), jeśli zawiera spację.|  
|`identifier`|Opcjonalny. Nazwa logiczna zasobu; Nazwa użyta do załadowania. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy zasób jest publiczny, czy prywatny w manifeście zestawu, tak jak w przypadku następujących wartości: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `-linkresource`, aby połączyć zasób z zestawem bez umieszczania pliku zasobów w pliku wyjściowym.  
  
 Jeśli `filename` to .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w przestrzeni nazw <xref:System.Resources> (zobacz <xref:System.Resources.ResourceManager>, aby uzyskać więcej informacji). Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Krótka forma `-resource` jest `-res`.  
  
 Aby uzyskać informacje na temat sposobu ustawiania `-resource` w środowisku IDE programu Visual Studio, zobacz [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik zasobów `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
