---
title: Typizowane elementy DataSet
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 7c8111e0e62a57b6745a5ea0387fc65a05839df8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785838"
---
# <a name="typed-datasets"></a>Typizowane elementy DataSet
Wraz z późnym wiązaniem dostępu do wartości za pomocą zmiennych o nieprawidłowym typie, <xref:System.Data.DataSet> zapewnia dostęp do danych przez silnie wpisaną metaphor. Do tabel i kolumn, które są częścią **zestawu danych** , można uzyskać dostęp przy użyciu nazw przyjaznych dla użytkownika i silnie wpisanych zmiennych.  
  
 Typ **DataSet** jest klasą pochodzącą z **zestawu danych**. W związku z tym dziedziczy wszystkie metody, zdarzenia i właściwości **zestawu danych**. Ponadto typ **DataSet** zawiera silnie wpisane metody, zdarzenia i właściwości. Oznacza to, że można uzyskać dostęp do tabel i kolumn według nazwy, zamiast korzystać z metod opartych na kolekcji. Oprócz ulepszonego czytelności kodu, wpisany **zestaw danych** umożliwia również edytorowi kodu Visual Studio .net automatyczne uzupełnianie wierszy podczas pisania.  
  
 Ponadto **zestaw danych** o jednoznacznie określonym typie zapewnia dostęp do wartości jako poprawnego typu w czasie kompilacji. Przy użyciu silnie określonego **zestawu danych**błędy niezgodności typów są przechwytywane podczas kompilowania kodu, a nie w czasie wykonywania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie silnie typizowanych elementów DataSet](generating-strongly-typed-datasets.md)  
 Opisuje sposób tworzenia i używania silnie określonego **zestawu danych**.  
  
 [Dodawanie adnotacji do typizowanych elementów DataSet](annotating-typed-datasets.md)  
 Opisuje sposób dodawania adnotacji do schematu języka definicji schematu XML (XSD) używanego do generowania **zestawu danych**o jednoznacznie określonym typie, aby nadać elementom **DataSet** przyjazne nazwy bez modyfikowania bazowego schematu.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
