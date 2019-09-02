---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202908"
---
# <a name="-c-compiler-options"></a>@ (opcje kompilatora C#)
Opcja @ pozwala określić plik, który zawiera opcje kompilatora i pliki kodu źródłowego do skompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.  
  
## <a name="remarks"></a>Uwagi  
 Opcje kompilatora i pliki kodu źródłowego będą przetwarzane przez kompilator tak, jakby zostały określone w wierszu polecenia.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, określ wiele opcji plików odpowiedzi. Na przykład:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 W pliku odpowiedzi w jednym wierszu może znajdować się wiele opcji kompilatora i plików kodu źródłowego. Jedna Specyfikacja opcji kompilatora musi znajdować się w jednym wierszu (nie może obejmować wielu wierszy). Pliki odpowiedzi mogą mieć komentarze zaczynające się od znaku #.  
  
 Określanie opcji kompilatora z poziomu pliku odpowiedzi jest tak samo samo jak wydawanie tych poleceń w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Kompilowanie z wiersza polecenia](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) .  
  
 Kompilator przetwarza opcje polecenia w miarę ich napotkania. W związku z tym argumenty wiersza polecenia mogą przesłonić wcześniej wymienione opcje w plikach odpowiedzi. Z kolei opcje w pliku odpowiedzi zastępują opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.  
  
 C#udostępnia plik csc. rsp, który znajduje się w tym samym katalogu, co plik csc. exe. Aby uzyskać więcej informacji na temat CSC. rsp, zobacz [-noconfig](./noconfig-compiler-option.md) .  
  
 Nie można ustawić tej opcji kompilatora w środowisku deweloperskim programu Visual Studio, ani programowo zmienić.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kilka wierszy z przykładowego pliku odpowiedzi:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
