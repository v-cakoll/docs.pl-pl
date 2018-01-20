---
title: '@ (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbb95e0619857f38260ae74366ba4bb860779530
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-c-compiler-options"></a>@ (opcje kompilatora C#)
@ — Opcja pozwala określić plik, który zawiera opcje kompilatora i plików kodu źródłowego do skompilowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumenty  
 `response_file`  
 Plik, który zawiera listę opcji kompilatora lub plików kodu źródłowego do skompilowania.  
  
## <a name="remarks"></a>Uwagi  
 Opcje kompilatora i plików kodu źródłowego zostanie przetworzony przez kompilator tak, jakby były one określone w wierszu polecenia.  
  
 Aby określić więcej niż jeden plik odpowiedzi w kompilacji, należy określić wiele opcji pliku odpowiedzi. Na przykład:  
  
```  
@file1.rsp @file2.rsp  
```  
  
 W odpowiedzi na plik, wiele opcji kompilatora i plików kodu źródłowego może występować w jednym wierszu. Specyfikacja opcji kompilatora pojedynczego musi znajdować się w jednym wierszu (nie może obejmować wiele wierszy). Pliki odpowiedzi mogą mieć komentarze, które zaczynają się od symbolu #.  
  
 Określenie opcji kompilatora z pliku odpowiedzi jest podobnie jak wystawiania tych poleceń w wierszu polecenia. Zobacz [tworzenie z wiersza polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) Aby uzyskać więcej informacji.  
  
 Kompilator przetwarza opcji polecenia, ponieważ są one napotkał. W związku z tym argumenty wiersza polecenia można zastąpić opcje wymienione wcześniej w plikach odpowiedzi. Z drugiej strony Opcje w pliku odpowiedzi zastąpią opcje wymienione wcześniej w wierszu polecenia lub w innych plików odpowiedzi.  
  
 C# zawiera pliku csc.rsp, który znajduje się w tym samym katalogu co plik csc.exe. Zobacz [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Aby uzyskać więcej informacji na temat csc.rsp.  
  
 Tej opcji kompilatora nie można ustawić w środowisku programowania Visual Studio i nie można go zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono kilka wierszy z przykładowy plik odpowiedzi:  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
