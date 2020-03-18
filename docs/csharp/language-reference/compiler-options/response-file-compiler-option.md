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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202908"
---
# <a name="-c-compiler-options"></a>@ (opcje kompilatora C#)
Opcja @ umożliwia określenie pliku zawierającego opcje kompilatora i pliki kodu źródłowego do skompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.  
  
## <a name="remarks"></a>Uwagi  
 Opcje kompilatora i pliki kodu źródłowego będą przetwarzane przez kompilator tak, jakby zostały określone w wierszu polecenia.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, określ wiele opcji pliku odpowiedzi. Przykład:  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 W pliku odpowiedzi wiele opcji kompilatora i plików kodu źródłowego może pojawić się w jednym wierszu. Specyfikacja opcji pojedynczego kompilatora musi pojawić się w jednym wierszu (nie może zawierać wielu wierszy). Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od symbolu #.  
  
 Określanie opcji kompilatora z pliku odpowiedzi jest jak wydawanie tych poleceń w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Tworzenie z wiersza polecenia.](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
  
 Kompilator przetwarza opcje polecenia, ponieważ są one napotkane. W związku z tym argumenty wiersza polecenia można zastąpić wcześniej wymienionych opcji w plikach odpowiedzi. Z drugiej strony opcje w pliku odpowiedzi zastąpią opcje wymienione wcześniej w wierszu polecenia lub w innych plikach odpowiedzi.  
  
 C# udostępnia plik csc.rsp, który znajduje się w tym samym katalogu co plik csc.exe. Zobacz [-noconfig](./noconfig-compiler-option.md) aby uzyskać więcej informacji na temat csc.rsp.  
  
 Nie można ustawić tej opcji kompilatora w środowisku programistycznym programu Visual Studio ani nie można jej programowo zmienić.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kilka wierszy z przykładowego pliku odpowiedzi:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
