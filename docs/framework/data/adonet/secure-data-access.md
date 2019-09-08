---
title: Bezpieczny dostęp do danych
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: 122bdaf8467994f8f56ce3f6c92457be6b8b3155
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782777"
---
# <a name="secure-data-access"></a>Bezpieczny dostęp do danych
Aby napisać bezpieczny kod ADO.NET, należy zapoznać się z mechanizmami zabezpieczeń dostępnymi w podstawowym magazynie danych lub w bazie danych. Należy również wziąć pod uwagę implikacje zabezpieczeń innych funkcji lub składników, które może zawierać aplikacja.  
  
## <a name="authentication-authorization-and-permissions"></a>Uwierzytelnianie, autoryzacja i uprawnienia  
 Podczas nawiązywania połączenia z usługą Microsoft SQL Server można używać uwierzytelniania systemu Windows, znanego również jako zabezpieczenia zintegrowane, które korzysta z tożsamości bieżącego aktywnego użytkownika systemu Windows zamiast przekazywania identyfikatora użytkownika i hasła. Korzystanie z uwierzytelniania systemu Windows jest zdecydowanie zalecane, ponieważ poświadczenia użytkownika nie są ujawniane w parametrach połączenia. Jeśli nie można użyć uwierzytelniania systemu Windows w celu nawiązania połączenia z SQL Server, rozważ utworzenie parametrów połączenia w czasie <xref:System.Data.SqlClient.SqlConnectionStringBuilder>wykonywania przy użyciu.  
  
 Poświadczenia używane do uwierzytelniania muszą być obsługiwane w różny sposób w zależności od typu aplikacji. Na przykład w aplikacji Windows Forms użytkownik może zostać poproszony o podanie informacji dotyczących uwierzytelniania lub można użyć poświadczeń systemu Windows użytkownika. Jednak aplikacja sieci Web często uzyskuje dostęp do danych przy użyciu poświadczeń dostarczonych przez samą aplikację, a nie przez użytkownika.  
  
 Po uwierzytelnieniu użytkowników zakres ich działań zależy od uprawnień, które zostały im przyznane. Zawsze stosuj zasadę najniższych uprawnień i przyznaj tylko uprawnienia, które są absolutnie niezbędne.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Ochrona informacji o połączeniu](protecting-connection-information.md)|Opisuje najlepsze rozwiązania w zakresie zabezpieczeń i techniki ochrony informacji o połączeniach, takich jak używanie konfiguracji chronionej do szyfrowania parametrów połączenia.|  
|[Zalecenia dotyczące strategii dostępu do danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywania operacji bazy danych.|  
|[Konstruktorzy parametrów połączeń](connection-string-builders.md)|Opisuje sposób tworzenia parametrów połączenia z danych wejściowych użytkownika w czasie wykonywania.|  
|[Przegląd zabezpieczeń serwera SQL](./sql/overview-of-sql-server-security.md)|Opisuje SQL Server architekturę zabezpieczeń.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Polecenia sparametryzowane i iniekcja kodu SQL  
 Używanie sparametryzowanych poleceń pomaga chronić przed atakami polegającymi na iniekcji SQL, w których osoba atakująca "wprowadza" polecenie do instrukcji SQL, która narusza zabezpieczenia na serwerze. Sparametryzowane polecenia Guard przed atakami polegającymi na iniekcji SQL przez zapewnienie, że wartości otrzymywane ze źródła zewnętrznego są przesyłane jako tylko wartości, a nie częścią instrukcji języka Transact-SQL. W związku z tym polecenia języka Transact-SQL wstawione do wartości nie są wykonywane w źródle danych. Zamiast tego są oceniane wyłącznie jako wartość parametru. Oprócz korzyści z zabezpieczeń, polecenia sparametryzowane zapewniają wygodną metodę organizowania wartości przekazaną za pomocą instrukcji języka Transact-SQL lub procedury składowanej.  
  
 Aby uzyskać więcej informacji na temat korzystania z sparametryzowanych poleceń, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Parametry elementu DataAdapter](dataadapter-parameters.md)|Opisuje sposób używania parametrów z `DataAdapter`.|  
|[Modyfikowanie danych za pomocą procedur składowanych](modifying-data-with-stored-procedures.md)|Opisuje sposób określania parametrów i uzyskiwania wartości zwracanej.|  
|[Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](./sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Opisuje sposób korzystania z procedur składowanych SQL Server w celu hermetyzacji dostępu do danych.|  
  
## <a name="script-exploits"></a>Luki w zabezpieczeniach skryptów  
 Wykorzystanie skryptów jest kolejną formą iniekcji, która używa złośliwych znaków wstawianych do strony sieci Web. Przeglądarka nie sprawdza poprawności wstawionych znaków i przetworzy je jako część strony.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Omówienie luk w zabezpieczeniach](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Opisuje sposób zabezpieczania przed skryptami i programami wykorzystującymi luki w zabezpieczeniach języka SQL.|  
  
## <a name="probing-attacks"></a>Ataki na sondowanie  
 Osoby atakujące często wykorzystują informacje z wyjątku, takie jak nazwa serwera, bazy danych lub tabeli, w celu zainstalowania ataku w systemie. Ponieważ wyjątki mogą zawierać określone informacje o aplikacji lub źródle danych, można pomóc zapewnić lepszą ochronę aplikacji i źródła danych przez ujawnienie do klienta najważniejszych informacji.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podstawy obsługi wyjątków](../../../standard/exceptions/exception-handling-fundamentals.md)|Opisuje podstawowe formy obsłudze wyjątków try/catch/finally.|  
|[Najlepsze rozwiązania dotyczące wyjątków](../../../standard/exceptions/best-practices-for-exceptions.md)|W tym artykule opisano najlepsze rozwiązania dotyczące obsługi wyjątków.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Ochrona dostępu do źródeł danych programu Microsoft Access i programu Excel  
 Program Microsoft Access i program Microsoft Excel mogą działać jako magazyn danych dla aplikacji ADO.NET, gdy wymagania dotyczące zabezpieczeń są minimalne lub nieistniejące. Ich funkcje zabezpieczeń są skuteczne dla Deterrence, ale nie powinny być używane na potrzeby wykonywania więcej niż zniechęcić meddling przez użytkowników nieposiadających informacji. Pliki danych fizycznych dla programu Access i programu Excel istnieją w systemie plików i muszą być dostępne dla wszystkich użytkowników. Sprawia to, że są one podatne na ataki, które mogą spowodować kradzież lub utratę danych, ponieważ pliki mogą być łatwo kopiowane lub zmieniane. Gdy wymagane są niezawodne zabezpieczenia, należy użyć SQL Server lub innej bazy danych opartej na serwerze, w której pliki danych fizycznych nie są odczytywane z systemu plików.  
  
 Aby uzyskać więcej informacji na temat ochrony dostępu i danych programu Excel, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zagadnienia dotyczące zabezpieczeń i wskazówki dotyczące dostępu 2007](https://go.microsoft.com/fwlink/?LinkId=98354)|Opisuje techniki zabezpieczeń dotyczące dostępu 2007, takich jak szyfrowanie plików, administrowanie hasłami, konwertowanie baz danych do nowych formatów ACCDB i ACCDe oraz korzystanie z innych opcji zabezpieczeń.|  
|[Informacje o roli plików informacyjnych grupy roboczej w zabezpieczeniach dostępu](https://support.microsoft.com/kb/305542)|Wyjaśnia rolę i relację pliku informacji o grupie roboczej w programie Access 2003 zabezpieczenia.|  
|[Często zadawane pytania dotyczące zabezpieczeń programu Microsoft Access dla programu Microsoft Access w wersji 2,0 do 2000](https://go.microsoft.com/fwlink/?LinkId=47698)|Wersja do pobrania, często zadawane pytania dotyczące zabezpieczeń programu Microsoft Access.|  
## <a name="enterprise-services"></a>Enterprise Services  
 COM+ zawiera własny model zabezpieczeń, który opiera się na kontach systemu Windows NT i personifikacji procesu/wątku. Przestrzeń nazw zawiera otoki, które umożliwiają aplikacjom .NET integrację kodu zarządzanego z usługami zabezpieczeń modelu <xref:System.EnterpriseServices.ServicedComponent> com+ za pomocą klasy. <xref:System.EnterpriseServices>  
  
 Aby uzyskać więcej informacji, zobacz następujący zasób.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zabezpieczenia oparte na rolach](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/s6y8k15h(v=vs.71))|W tym artykule omówiono sposób integrowania kodu zarządzanego z usługami zabezpieczeń modelu COM+.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym  
 .NET Framework zapewnia interakcję z niezarządzanym kodem, w tym składniki COM, usługi COM+, zewnętrzne biblioteki typów i wiele usług systemu operacyjnego. Praca z kodem niezarządzanym polega na przejściu poza obwód zabezpieczeń dla kodu zarządzanego. Zarówno kod, jak i dowolny kod, który wywołuje go musi mieć uprawnienia<xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> do kodu niezarządzanego (z określoną flagą). Kod niezarządzany może wprowadzić niezamierzone luki w zabezpieczeniach do aplikacji. W związku z tym należy unikać współdziałania z kodem niezarządzanym, chyba że jest to absolutnie konieczne.  
  
 Aby uzyskać więcej informacji, zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Współdziałanie z kodem niezarządzanym](../../interop/index.md)|Zawiera tematy opisujące, jak uwidocznić składniki COM w .NET Framework i jak uwidocznić składniki .NET Framework do modelu COM.|
|[Zaawansowana współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Zawiera zaawansowane tematy, takie jak podstawowe zestawy międzyoperacyjności, wątkowość i organizowanie niestandardowe.|

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Zabezpieczenia serwera SQL](./sql/sql-server-security.md)
- [Zalecenia dotyczące strategii dostępu do danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Ochrona informacji o połączeniu](protecting-connection-information.md)
- [Konstruktorzy parametrów połączeń](connection-string-builders.md)
- [Omówienie ADO.NET](ado-net-overview.md)
