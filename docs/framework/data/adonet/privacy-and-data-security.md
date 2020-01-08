---
title: Bezpieczeństwo danych i poufności informacji
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: a8d7ae2ece966b4649c9c988c123304fe3f1b4d9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348138"
---
# <a name="privacy-and-data-security"></a>Bezpieczeństwo danych i poufności informacji
Zabezpieczanie poufnych informacji w aplikacji ADO.NET i zarządzanie nimi zależy od podstawowych produktów i technologii użytych do jego utworzenia. Usługa ADO.NET nie udostępnia bezpośrednio usług służących do zabezpieczania i szyfrowania danych.  
  
## <a name="cryptography-and-hash-codes"></a>Kody kryptografii i wartości skrótu  
 Klasy w przestrzeni nazw <xref:System.Security.Cryptography> .NET Framework mogą być używane z poziomu aplikacji ADO.NET, aby uniemożliwić odczytywanie i modyfikowanie danych przez nieautoryzowane strony trzecie. Niektóre klasy są otokami dla niezarządzanego interfejsu CryptoAPI firmy Microsoft, podczas gdy inne są wdrożeniami zarządzanymi. Temat [usługi kryptograficzne](../../../standard/security/cryptographic-services.md) zawiera omówienie kryptografii w .NET Framework, opis sposobu implementacji cryptograph oraz sposób wykonywania określonych zadań kryptograficznych.  
  
 W przeciwieństwie do kryptografii, która umożliwia szyfrowanie i odszyfrowywanie danych, dane mieszania są procesem jednokierunkowym. Dane dotyczące mieszania są przydatne, gdy chcesz zapobiec naruszeniu przez sprawdzenie, czy dane nie zostały zmienione: dane wejściowe są identyczne, algorytmy wyznaczania wartości skrótu zawsze generują identyczne krótkie wartości wyjściowe, które można łatwo porównać. [Zapewnianie integralności danych za pomocą kodów skrótów](../../../standard/security/ensuring-data-integrity-with-hash-codes.md) opisuje sposób generowania i weryfikowania wartości skrótu.  
  
## <a name="encrypting-configuration-files"></a>Szyfrowanie plików konfiguracji  
 Ochrona dostępu do źródła danych jest jednym z najważniejszych celów związanych z zabezpieczaniem aplikacji. Parametry połączenia przedstawiają potencjalną lukę w zabezpieczeniach, jeśli nie została zabezpieczona. Parametry połączenia zapisane w plikach konfiguracji są przechowywane w standardowych plikach XML, dla których .NET Framework zdefiniował wspólny zestaw elementów. Konfiguracja chroniona umożliwia szyfrowanie poufnych informacji w pliku konfiguracji. Program, który jest przeznaczony głównie do aplikacji ASP.NET, może być również używany do szyfrowania sekcji plików konfiguracyjnych w aplikacjach systemu Windows. Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpieczanie wartości ciągu w pamięci  
 Jeśli obiekt <xref:System.String> zawiera informacje poufne, takie jak hasło, numer karty kredytowej lub dane osobowe, istnieje ryzyko, że te informacje mogą być ujawnione po ich użyciu, ponieważ aplikacja nie może usunąć danych z pamięci komputera.  
  
 <xref:System.String> jest niemodyfikowalny; nie można zmodyfikować jego wartości po jej utworzeniu. Zmiany, które pojawiają się w celu zmodyfikowania wartości ciągu, w rzeczywistości tworzą nowe wystąpienie obiektu <xref:System.String> w pamięci, przechowując dane jako zwykły tekst. Ponadto nie można przewidzieć, kiedy wystąpienia ciągu zostaną usunięte z pamięci. Odzyskiwanie pamięci z użyciem ciągów nie jest deterministyczne przy użyciu wyrzucania elementów bezużytecznych platformy .NET. Należy unikać używania klas <xref:System.String> i <xref:System.Text.StringBuilder>, jeśli dane są naprawdę poufne.  
  
 Klasa <xref:System.Security.SecureString> zapewnia metody szyfrowania tekstu przy użyciu interfejsu API ochrony danych (DPAPI) w pamięci. Ten ciąg jest następnie usuwany z pamięci, gdy nie jest już wymagany. Nie ma `ToString` metody, aby szybko odczytać zawartość <xref:System.Security.SecureString>. Można zainicjować nowe wystąpienie `SecureString` bez wartości lub przekazując wskaźnik do tablicy obiektów <xref:System.Char>. Następnie można użyć różnych metod klasy do pracy z ciągiem.
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Zabezpieczenia serwera SQL](./sql/sql-server-security.md)
- [Omówienie ADO.NET](ado-net-overview.md)
