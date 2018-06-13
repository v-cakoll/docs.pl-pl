---
title: Pojęcia dotyczące serializacji
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: f16de0e95f7520e377dc9920743261ad6019e430
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583763"
---
# <a name="serialization-concepts"></a>Pojęcia dotyczące serializacji
Dlaczego czy chcesz użyć serializacji? Dwie najważniejsze przyczyny są, aby zachować stan obiektu na nośniku, dokładna kopia może zostać ponownie utworzone na późniejszym etapie, a aby wysłać obiekt przez wartość z domeny w jednej aplikacji na inny. Na przykład serializacji służy do zapisywania stanu sesji w programie ASP.NET i skopiować obiekty do Schowka w formularzach systemu Windows. On również używany łącząc do przekazywania obiektów przez wartość z domeny jedną aplikację do innego.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Trwałego magazynu
Często jest to niezbędne do przechowywania wartości pól obiektu na dysku, a następnie później, pobrania tych danych. Jest to łatwa do osiągnięcia bez polegania na serializacji, ta metoda jest często skomplikowane i błąd podatnych na błędy i staje się stopniowo bardziej złożone, gdy zachodzi potrzeba śledzenia hierarchii obiektów. Wyobraź sobie aplikacji dużych firm, który zawiera tysiące obiektów, zapisywania i konieczności pisania kodu do zapisywania i przywracania pola i właściwości do i z dysku dla każdego obiektu. Serializacja oferuje wygodny mechanizm do osiągnięcia tego celu.

Środowisko uruchomieniowe języka wspólnego zarządza, w jaki sposób obiekty są przechowywane w pamięci i udostępnia mechanizm serializacji zautomatyzowanych za pomocą [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md). Gdy obiekt jest serializowany, nazwa klasy, zestaw i wszystkie składowe danych wystąpienia klasy są zapisywane w pamięci masowej. Obiekty przechowywania często odwołuje się do innych wystąpień w zmiennych elementu członkowskiego. Klasa jest serializowana, mechanizm serializacji śledzi występujących w odwołaniu dla obiektów, już, aby upewnić się, że ten sam obiekt nie jest serializowana więcej niż raz. Architektura serializacji dołączonym do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] poprawnie obsługuje wykresy i obiektów odwołania cykliczne automatycznie. Jedynym wymaganiem dotyczącymi wykresów obiektów jest, że wszystkie obiekty odwołuje się Zserializowany obiekt musi być oznaczona jako `Serializable` (Aby uzyskać więcej informacji, zobacz [podstawowe serializacji](basic-serialization.md)). Jeśli nie jest to wykonywane, zostanie zwrócony wyjątek serializator próba serializacji obiektu nieoznaczone.

Podczas deserializacji jest klasa serializacji, zostaje odtworzone klasy i automatycznie zostaną przywrócone wartości wszystkich elementów członkowskich danych.

## <a name="marshal-by-value"></a>Kierowanie przez wartość
Obiekty są prawidłowe tylko w domenie aplikacji, w którym zostały utworzone. Każda próba przekazania obiektu jako parametr lub przywrócić go w związku z tym zakończy się niepowodzeniem, chyba że obiekt jest pochodną `MarshalByRefObject` lub jest oznaczony jako `Serializable`. Jeśli obiekt jest oznaczona jako `Serializable`, obiekt zostanie automatycznie serializacji, transportowane z domeny w jednej aplikacji do innych i następnie deserializowany, aby wygenerować dokładne kopię obiektu w drugiej domenie aplikacji. Ten proces jest zwykle określany jako marshal przez wartość.
 
Gdy obiekt jest pochodną `MarshalByRefObject`, odwołanie do obiektu jest przekazywany z aplikacji jednej domeny do innej domeny, a nie samego obiektu. Można również oznaczyć obiektu pochodzącego od `MarshalByRefObject` jako `Serializable`. Jeśli ten obiekt jest używany z usług zdalnych, element formatujący odpowiedzialny za serializacji, wstępnie z selektorem dwuskładnikowego (`SurrogateSelector`), przejmuje kontrolę nad procesu serializacji i zastępuje wszystkie obiekty pochodne `MarshalByRefObject` z Serwer proxy. Bez `SurrogateSelector` w miejscu, architektura serializacji regułom standardowe serializacji opisanego w [kroki w procesie serializacji](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Sekcje pokrewne  
 [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
 Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.  
  
 [Obiekty zdalnego](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.  
  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.
