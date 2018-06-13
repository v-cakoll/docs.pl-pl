---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9c854060e5254cedc6c1004ac3e4f25fbdbbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650670"
---
# <a name="-filealign"></a>-filealign
Określa lokalizację były wyrównane w sekcjach pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wymagana. Wartość, która określa sposób wyrównania sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 do 8192. Te wartości są w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `-filealign` opcję, aby określić wyrównanie sekcji w pliku danych wyjściowych. Sekcje są bloków pamięci ciągłej w pliku przenośnym plikiem wykonawczym (PE), który zawiera kod lub dane. `-filealign` Opcja umożliwia kompilowanie aplikacji przy użyciu niestandardowych wyrównanie; większość deweloperów nie trzeba używać tej opcji.  
  
 Każda sekcja jest wyrównany na granicy, która jest wielokrotnością liczby `-filealign` wartość. Nie jest domyślnie stałym. Jeśli `-filealign` nie zostanie określony, kompilator wybiera domyślny, w czasie kompilacji.  
  
 Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego. Modyfikowanie rozmiar sekcji mogą być przydatne dla programów uruchamianych na mniejsze urządzenia.  
  
> [!NOTE]
>  `-filealign` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
