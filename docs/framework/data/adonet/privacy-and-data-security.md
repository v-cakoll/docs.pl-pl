---
title: Prywatność i bezpieczeństwo danych
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: 078b5e09e800511c3edfa78596b5bdb67ebcc6d7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194933"
---
# <a name="privacy-and-data-security"></a>Prywatność i bezpieczeństwo danych
Zabezpieczenia i zarządzanie nimi poufnych informacji w aplikacji ADO.NET zależy od bazowego produkty i technologie używane do jego utworzenia. ADO.NET nie są bezpośrednio dostępne usługi dla zabezpieczenia i szyfrowanie danych.  
  
## <a name="cryptography-and-hash-codes"></a>Kryptografii i kodów skrótów  
 Klasy w .NET Framework <xref:System.Security.Cryptography> przestrzeni nazw można z poziomu aplikacji ADO.NET danych odczytu i modyfikacji nieautoryzowanym osobom trzecim. Niektóre klasy są otoki dla niezarządzanych CryptoAPI firmy Microsoft, a inne implementacje zarządzanych. [Usługi kryptograficzne](../../../../docs/standard/security/cryptographic-services.md) temat zawiera omówienie kryptografii w programie .NET Framework, w tym artykule opisano sposób implementacji cryptograph i sposobu wykonywania określonych zadań kryptograficznych.  
  
 W przeciwieństwie do szyfrowania, który pozwala na być szyfrowane, a następnie odszyfrować danych, tworzenia skrótu danych jest procesem jednokierunkowym. Mieszania danych jest przydatne, jeśli chcesz zapobiec modyfikowaniu, sprawdzając, czy dane nie zostały zmienione: podana identyczne ciągi wejściowe, algorytmy wyznaczania wartości skrótu zawsze produkcji wartości identyczny krótkich danych wyjściowych, które można łatwo porównać. [Zapewnianie integralności danych za pomocą wartości skrótu](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) opisuje sposób generowania i sprawdź wartości skrótu.  
  
## <a name="encrypting-configuration-files"></a>Szyfrowanie plików konfiguracji  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów podczas zabezpieczania aplikacji. Parametry połączenia przedstawia informacje o potencjalnych luk w zabezpieczeniach, jeśli nie jest zabezpieczony. Parametry połączenia, zapisane w plikach konfiguracji są przechowywane w standardowymi plikami XML, dla których programu .NET Framework został zdefiniowany zestaw wspólnych elementów. Chronione konfiguracji umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Mimo że przeznaczony głównie dla aplikacji ASP.NET, konfiguracji chronionych można również do szyfrowania sekcji pliku konfiguracji w aplikacji Windows. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpieczanie wartości ciągu w pamięci  
 Jeśli <xref:System.String> obiekt zawiera poufne informacje, takie jak hasła, numer karty kredytowej lub dane osobowe, istnieje ryzyko, że informacje mogą być ujawniło, gdy jest używane, ponieważ aplikacja nie może usunąć dane z pamięci komputera.  
  
 Element <xref:System.String> można modyfikować; nie można zmodyfikować jego wartości, po jego utworzeniu. Zmiany, które są wyświetlane, aby zmodyfikować wartość ciągu tworzą nowe wystąpienie klasy <xref:System.String> obiektu w pamięci, przechowywanie danych w postaci zwykłego tekstu. Ponadto nie jest możliwość przewidywanie, kiedy wystąpienia ciągu zostanie on usunięty z pamięci. Odzyskiwanie pamięci z ciągami nie jest jednoznaczny przy użyciu platformy .NET wyrzucania elementów bezużytecznych. Należy unikać używania <xref:System.String> i <xref:System.Text.StringBuilder> klasy, jeśli dane są naprawdę ważne.  
  
 <xref:System.Security.SecureString> Klasa dostarcza metody do szyfrowania tekstu w pamięci przy użyciu interfejsu API ochrony danych (DPAPI). Ten ciąg jest usuwany z pamięci, gdy nie jest już potrzebny. Istnieje nie `ToString` metodę, aby szybko zapoznać się zawartość <xref:System.Security.SecureString>. Można zainicjować nowe wystąpienie klasy `SecureString` bez wartości lub przez przekazanie jej wskaźnik do tablicy <xref:System.Char> obiektów. Można następnie użyć różnych metod klasy do pracy z ciągu. Aby uzyskać więcej informacji, Pobierz [SecureString przykładowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=120418), który demonstruje sposób skorzystania `SecureString` klasy z.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
