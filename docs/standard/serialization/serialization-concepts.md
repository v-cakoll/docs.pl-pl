---
title: Pojęcia dotyczące serializacji
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 99716a6346689ac4d3201f83b0b8204cad462e8e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593323"
---
# <a name="serialization-concepts"></a>Pojęcia dotyczące serializacji
Dlaczego czy chcesz użyć serializacji? Dwie najważniejsze przyczyny są do utrwalenia stanu obiektu na nośniku, więc dokładna kopia może być utworzony ponownie w późniejszym terminie, a aby wysłać obiekt według wartości z jednej aplikacji domeny do innego. Na przykład serializacji jest używany do zapisywania stanu sesji na platformie ASP.NET i skopiować obiekty do Schowka w formularzach Windows Forms. Również służy przez zdalnych do przekazywania obiektów według wartości z jednej aplikacji domeny do innego.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Magazyn trwały
Często jest to niezbędne do przechowywania wartości pól obiektu na dysku, a następnie później, pobrania tych danych. Chociaż jest to łatwe do osiągnięcia bez polegania na serializacji, ta metoda jest często skomplikowana względem i podatne, błąd i staje się stopniowo bardziej złożonych, gdy zachodzi potrzeba śledzenia hierarchii obiektów. Wyobraź sobie pisania aplikacji sieci dużych firm, który zawiera tysiące obiektów, i konieczności pisania kodu do zapisywania i przywracania pola i właściwości, do i z dysku dla każdego obiektu. Serializacja oferuje wygodny mechanizm do osiągnięcia tego celu.

Środowisko uruchomieniowe języka wspólnego zarządza, jak obiekty są przechowywane w pamięci i udostępnia mechanizm serializacji automatyczne przy użyciu [odbicia](../../../docs/framework/reflection-and-codedom/reflection.md). Gdy obiekt jest serializowany, nazwa klasy, zestaw i wszystkie składowe danych wystąpienia klasy są zapisywane w pamięci masowej. Obiekty przechowywania często odwołuje się do innych wystąpień w zmiennych elementu członkowskiego. Klasa jest serializowana, mechanizm serializacji śledzi występujących w odwołaniu dla obiektów, już, aby upewnić się, że ten sam obiekt nie jest serializowana więcej niż raz. Architektura serializacji udostępniała za pomocą programu .NET Framework poprawnie obsługuje wykresy i obiektów odwołania cykliczne automatycznie. Jedynym wymaganiem umieszczony na obiekcie wykresy jest, że wszystkie obiekty, odwołuje się Zserializowany obiekt musi być oznaczona jako `Serializable` (Aby uzyskać więcej informacji, zobacz [podstawowe serializacji](basic-serialization.md)). Jeśli nie jest to wykonywane, zostanie zwrócony wyjątek serializator próba serializacji obiektu nieoznaczone.

Podczas deserializacji jest klasa serializacji, jest ponownie utworzyć klasę i wartości wszystkich składowych danych zostaną automatycznie przywrócone.

## <a name="marshal-by-value"></a>Kierować według wartości
Obiekty są prawidłowe tylko w domenie aplikacji, w którym zostały utworzone. Każda próba przekazania obiektu jako parametr lub przywrócić go w wyniku zakończy się niepowodzeniem, chyba że pochodzi od klasy obiektu `MarshalByRefObject` lub jest oznaczony jako `Serializable`. Jeśli obiekt jest oznaczony jako `Serializable`, obiekt zostanie automatycznie serializacji, transportowane z domeny jedną aplikację do drugiego i następnie deserializacji, aby utworzyć dokładną kopię obiektu w drugiej domenie aplikacji. Ten proces jest zwykle określany jako marshal przez wartość.
 
Jeśli obiekt pochodzi od klasy `MarshalByRefObject`, odwołanie do obiektu jest przekazywane z jednej aplikacji domeny do innej domeny, a nie samego obiektu. Można również zaznaczyć obiekt, który pochodzi od klasy `MarshalByRefObject` jako `Serializable`. Gdy ten obiekt jest używany z wywołaniem funkcji zdalnych, program formatujący odpowiedzialny za serializacji, który został wstępnie skonfigurowany z selektora znaków (`SurrogateSelector`), przyjmuje kontrolę nad procesem serializacji i zamienia wszystkie obiekty opracowane na podstawie `MarshalByRefObject` z Serwer proxy. Bez `SurrogateSelector` w miejscu, architektura serializacji regułom standardowe serializacji opisane w [kroki w procesie serializacji](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Sekcje pokrewne  
 [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
 Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.  
  
 [Wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
 Opis różnych metod komunikacji dostępnych w programie .NET Framework do komunikacji zdalnej.  
  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.
