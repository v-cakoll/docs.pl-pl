---
title: Tworzenie klasy utrzymującej funkcje DLL
description: Utwórz otokę zarządzanej klasy w programie .NET, aby przechowywać funkcje DLL, które ułatwiają hermetyzację funkcjonalności platformy.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622175"
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Tworzenie klasy utrzymującej funkcje DLL
Otoka często używanej funkcji DLL w klasie zarządzanej jest skutecznym podejściem do hermetyzacji funkcjonalności platformy. Chociaż nie jest to konieczne w każdym przypadku, zapewnienie otoki klasy jest wygodne, ponieważ Definiowanie funkcji DLL może być kłopotliwe i podatne na błędy. W przypadku programowania w Visual Basic lub C# należy zadeklarować funkcje DLL w ramach klasy lub modułu Visual Basic.  
  
 W obrębie klasy należy zdefiniować metodę statyczną dla każdej funkcji DLL, która ma zostać wywołana. Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub Konwencja wywoływania używana w argumentach metod przekazywania; Pomijając te informacje, należy wybrać ustawienia domyślne. Aby zapoznać się z pełną listą opcji deklaracji i ich ustawień domyślnych, zobacz [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).  
  
 Po zapakowaniu można wywołać metody klasy podczas wywoływania metod statycznych dla każdej innej klasy. Funkcja Invoke platformy obsługuje automatycznie wyeksportowaną funkcję.  
  
 Podczas projektowania zarządzanej klasy dla wywołania platformy należy wziąć pod uwagę relacje między klasami i funkcjami DLL. Możesz na przykład:  
  
- Deklarowanie funkcji DLL w obrębie istniejącej klasy.  
  
- Utwórz pojedynczą klasę dla każdej funkcji DLL, utrzymując funkcje izolowane i łatwe do odnalezienia.  
  
- Utwórz jedną klasę dla zestawu powiązanych funkcji DLL, aby tworzyć logiczne grupowania i zmniejszać obciążenie.  
  
 W tym celu można nazwać klasę i jej metody. Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)
- [Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md)
- [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
