---
title: 'Porady: przenoszenie danych do zmiennej i z niej'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bc5a7377a5e2e4c7ebe7291fd5f0093c4d6e996d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346902"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Porady: przenoszenie danych do zmiennej i z niej (Visual Basic)

Wartość jest przechowywana w zmiennej przez umieszczenie nazwy zmiennej po lewej stronie instrukcji przypisania.

## <a name="putting-data-in-a-variable"></a>Umieszczanie danych w zmiennej

#### <a name="to-store-a-value-in-a-variable"></a>Aby zapisać wartość w zmiennej

- Użyj nazwy zmiennej po lewej stronie instrukcji przypisania.

    Poniższy przykład ustawia wartość zmiennej `alpha`.

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    Wartość wygenerowana po prawej stronie instrukcji przypisania jest przechowywana w zmiennej.

## <a name="getting-data-from-a-variable"></a>Pobieranie danych ze zmiennej

Wartość zmiennej jest pobierana przez dołączenie nazwy zmiennej w wyrażeniu.

#### <a name="to-retrieve-a-value-from-a-variable"></a>Aby pobrać wartość ze zmiennej

- Użyj nazwy zmiennej w wyrażeniu. Możesz użyć zmiennej wszędzie tam, gdzie można użyć stałej lub literału, z wyjątkiem wyrażenia, które definiuje wartość stałej.

  \-lub-

- Użyj nazwy zmiennej po znaku równości (`=`) w instrukcji przypisania.

  Poniższy przykład odczytuje wartość zmiennej `startValue` a następnie używa wartości zmiennej `counter` w wyrażeniu.

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  Wartość zmiennej uczestniczy w wyrażeniu tak samo jak stała, a następnie jest przechowywana w zmiennej lub właściwości po lewej stronie instrukcji przypisania.

## <a name="see-also"></a>Zobacz także

- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
