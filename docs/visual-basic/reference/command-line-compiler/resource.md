---
title: -zasobów (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654440"
---
# <a name="-resource-visual-basic"></a>-zasobów (Visual Basic)
Osadza zarządzanego zasobu w zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Wymagana. Nazwa pliku zasobu do osadzenia w pliku wyjściowym. Domyślnie `filename` jest publiczny w zestawie. Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.|  
|`identifier`|Opcjonalna. Nazwa logiczna zasobu; Nazwa używana go załadować. Wartość domyślna to nazwa pliku. Opcjonalnie można określić, czy zasób jest publicznych lub prywatnych w manifeście zestawu następującym kodem: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `-linkresource` połączyć zasób zestawu bez wprowadzania do pliku zasobów w pliku wyjściowym.  
  
 Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw (zobacz <xref:System.Resources.ResourceManager> Aby uzyskać więcej informacji). Aby uzyskać dostęp do innych zasobów w czasie wykonywania, użyj jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 Krótka forma z `-resource` jest `-res`.  
  
 Aby uzyskać informacje dotyczące sposobu konfigurowania `-resource` w programie Visual Studio IDE, zobacz [zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik zasobu `Rf.resource`.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
