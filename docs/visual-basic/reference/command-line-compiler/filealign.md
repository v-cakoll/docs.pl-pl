---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a>/filealign
Określa lokalizację były wyrównane w sekcjach pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Wymagany. Wartość, która określa sposób wyrównania sekcji w pliku wyjściowym. Prawidłowe wartości to 512, 1024, 2048, 4096 do 8192. Te wartości są w bajtach.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `/filealign` opcję, aby określić wyrównanie sekcji w pliku danych wyjściowych. Sekcje są bloków pamięci ciągłej w pliku przenośnym plikiem wykonawczym (PE), który zawiera kod lub dane. `/filealign` Opcja umożliwia kompilowanie aplikacji przy użyciu niestandardowych wyrównanie; większość deweloperów nie trzeba używać tej opcji.  
  
 Każda sekcja jest wyrównany na granicy, która jest wielokrotnością liczby `/filealign` wartość. Nie jest domyślnie stałym. Jeśli `/filealign` nie zostanie określony, kompilator wybiera domyślny, w czasie kompilacji.  
  
 Określając rozmiar sekcji, można zmienić rozmiar pliku wyjściowego. Modyfikowanie rozmiar sekcji mogą być przydatne dla programów uruchamianych na mniejsze urządzenia.  
  
> [!NOTE]
>  `/filealign` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
