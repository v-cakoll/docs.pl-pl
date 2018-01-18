---
title: "Bezpieczeństwo danych i poufności informacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5c645b493a1ffb99f4d60f8011bc05f275b5d10f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="privacy-and-data-security"></a>Bezpieczeństwo danych i poufności informacji
Zabezpieczenia i zarządzanie poufnych informacji w aplikacji ADO.NET jest zależne od podstawowej produktów i technologii go utworzono. ADO.NET nie są bezpośrednio dostępne usługi dla zabezpieczanie lub szyfrowania danych.  
  
## <a name="cryptography-and-hash-codes"></a>Kryptografii i kodów skrótów  
 Klasy w programie .NET Framework <xref:System.Security.Cryptography> przestrzeni nazw może służyć z aplikacji ADO.NET danych do odczytu lub zmodyfikowane przez osoby nieupoważnione innych. Niektóre klasy są otoki dla niezarządzanego CryptoAPI firmy Microsoft, a inne implementacje zarządzanych. [Usługi kryptograficzne](http://msdn.microsoft.com/en-us/68a1e844-c63c-44af-9247-f6716eb23781) temat zawiera omówienie kryptografii w programie .NET Framework, w tym artykule opisano sposób implementacji cryptograph i sposobu wykonywania określonych zadań kryptograficznych.  
  
 W przeciwieństwie do szyfrowania, dzięki czemu dane powinny być szyfrowane i odszyfrowywane następnie, tworzenia skrótu danych jest procesem jednokierunkowym. Wyznaczania wartości skrótu danych jest przydatne, jeśli chcesz zapobiec modyfikowaniu przez sprawdzenie, czy dane nie zostały zmienione: podana identycznych ciągów wejściowych, algorytmami wyznaczania wartości skrótu zawsze powodowało identyczne dane wyjściowe krótkich wartości, które można łatwo porównać. [Zapewnianie integralności danych za pomocą wartości skrótu](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) opisano, jak można generować i weryfikować wartości skrótu.  
  
## <a name="encrypting-configuration-files"></a>System szyfrowania plików konfiguracji  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów zabezpieczania aplikacji. Ciąg połączenia przedstawia potencjalne luki w zabezpieczeniach, jeśli nie jest zabezpieczony. Parametry połączenia zapisywane w plikach konfiguracji są przechowywane w standardowe pliki XML, dla których programu .NET Framework został zdefiniowany zestaw wspólnych elementów. Chronione konfiguracji umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Chociaż przeznaczony głównie dla aplikacji ASP.NET, konfiguracji chronionych można również można zaszyfrować sekcji pliku konfiguracji w aplikacjach systemu Windows. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpieczanie wartości ciągu w pamięci  
 Jeśli <xref:System.String> obiektu zawiera poufne informacje, takie jak hasła, numer karty kredytowej lub dane osobowe, istnieje ryzyko, że informacje może być ujawniony po jest używany, ponieważ aplikacja nie może usunąć dane z pamięci komputera.  
  
 A <xref:System.String> jest niezmienialny; jego wartość nie może być modyfikowany, po jego utworzeniu. Zmiany, które są wyświetlane, aby zmodyfikować wartość ciągu, tworząc nowe wystąpienie klasy <xref:System.String> obiektu w pamięci, przechowywanie danych w postaci zwykłego tekstu. Ponadto nie jest możliwe do przewidzenia, gdy wystąpień ciągu zostanie usunięty z pamięci. Odzyskiwanie pamięci z ciągami nie jest deterministyczna z .NET wyrzucanie elementów bezużytecznych. Należy unikać używania <xref:System.String> i <xref:System.Text.StringBuilder> klasy, jeśli dane są naprawdę ważne.  
  
 <xref:System.Security.SecureString> Klasa dostarcza metody do szyfrowania tekstu w pamięci przy użyciu interfejsu API ochrony danych (DPAPI). Ten ciąg jest usuwany z pamięci nie jest już potrzebne. Brak nie `ToString` metodę, aby szybko odczytywać zawartość <xref:System.Security.SecureString>. Należy zainicjować nowe wystąpienie klasy `SecureString` bez wartości lub przez przekazanie jej wskaźnika do tablicy <xref:System.Char> obiektów. Można następnie użyć różnych metod klasy do pracy z ciągiem. Aby uzyskać więcej informacji, Pobierz [SecureString przykładowej aplikacji](http://go.microsoft.com/fwlink/?LinkId=120418), które przedstawiają sposób użycia `SecureString` klasę z.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
