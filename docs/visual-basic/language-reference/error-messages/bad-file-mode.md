---
title: Zły tryb pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409872"
---
# <a name="bad-file-mode"></a>Zły tryb pliku
Instrukcje używane podczas manipulowania zawartością pliku muszą być odpowiednie dla trybu, w którym plik został otwarty. Możliwe przyczyny są następujące:  
  
- `FilePutObject`Instrukcja or `FileGetObject` określa sekwencyjny plik.  
  
- `Print`Instrukcja Określa plik otwarty dla trybu dostępu innego niż `Output` lub `Append` .  
  
- `Input`Instrukcja Określa plik otwarty dla trybu dostępu innego niż`Input`  
  
- Próba zapisu w pliku tylko do odczytu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się `FilePutObject` , że `FileGetObject` odwołują się tylko do plików otwartych dla programu `Random` lub `Binary` .  
  
- Upewnij się, że `Print` określony plik jest otwarty w `Output` trybie obu lub `Append` dostępu. Jeśli nie, użyj innej instrukcji, aby umieścić dane w pliku, lub Otwórz ponownie plik w odpowiednim trybie.  
  
- Upewnij się `Input` , że wybrano plik otwarty dla programu `Input` . Jeśli nie, użyj innej instrukcji, aby umieścić dane w pliku, lub Otwórz ponownie plik w odpowiednim trybie.  
  
- Jeśli zapisujesz do pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie próbuj zapisywać do niego.  
  
- Użyj funkcji dostępnych w `My.Computer.FileSystem` obiekcie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileSystem>
- [Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
