---
title: Bezpieczny dostęp do danych
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: e5bb96a091dcd64f12d086d864643d00c34d8f17
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185943"
---
# <a name="secure-data-access"></a>Bezpieczny dostęp do danych
Aby pisać bezpieczny kod, ADO.NET, musisz znać mechanizmy zabezpieczeń dostępnych w podstawowym magazynie danych lub bazy danych. Należy również wziąć pod uwagę ryzyko związane z innych funkcji lub składniki, które Twoja aplikacja może zawierać.  
  
## <a name="authentication-authorization-and-permissions"></a>Uwierzytelnianie, autoryzacja i uprawnienia  
 Podczas nawiązywania połączenia z programem Microsoft SQL Server, można użyć uwierzytelniania Windows, znany także jako zintegrowanych zabezpieczeń, która korzysta z tożsamości w bieżącym aktywnym użytkownikiem Windows, a nie przekazywanie identyfikator użytkownika i hasło. Zdecydowanie zaleca korzystania z uwierzytelniania Windows, ponieważ poświadczenia użytkownika nie są widoczne w parametrach połączenia. Jeśli nie możesz użyć uwierzytelniania Windows do łączenia z programem SQL Server, rozważ tworzenia parametrów połączenia w czasie wykonywania za pomocą <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Poświadczenia używane do uwierzytelniania muszą być obsługiwane inaczej w zależności od typu aplikacji. Na przykład w aplikacji Windows Forms, użytkownik może być monit o podanie informacji uwierzytelniania lub poświadczenia Windows użytkownika mogą być używane. Jednak aplikacja sieci Web, który jest często uzyskuje dostęp do danych przy użyciu poświadczeń dostarczonych przez samą aplikację, a nie przez użytkownika.  
  
 Po uwierzytelnieniu użytkowników zakres ich działania zależą od uprawnień, którym przyznano im. Zawsze postępuj zgodnie z zasadą najniższych uprawnień i udzielić tylko te uprawnienia, które są jest to absolutnie konieczne.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)|W tym artykule opisano najlepsze rozwiązania dotyczące zabezpieczeń i technik do ochrony informacji o połączeniu, takich jak za pomocą konfiguracji chronionej do szyfrowania parametrów połączenia.|  
|[Zalecenia dotyczące strategii dostępu do danych](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywania operacji w bazie danych.|  
|[Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)|W tym artykule opisano sposób tworzenia parametrów połączenia z danych wejściowych użytkownika w czasie wykonywania.|  
|[Przegląd zabezpieczeń serwera SQL](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|W tym artykule opisano architekturę zabezpieczeń programu SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Sparametryzowanych poleceń i wstrzykiwanie kodu SQL  
 Używanie poleceń sparametryzowanych pomaga zabezpieczyć się przed atakami polegającymi na iniekcji SQL, w których osoba atakująca "wprowadza" polecenie do instrukcji SQL zabezpieczenia naruszeń na serwerze. Poleceń sparametryzowanych zabezpieczyć się przed ataku polegającego na iniekcji SQL, zapewniając, że wartości odebranych ze źródła zewnętrznego są przekazywane jako tylko wartości i nie jest częścią instrukcji języka Transact-SQL. W wyniku polecenia języka Transact-SQL do wartości nie są wykonywane w źródle danych. Przeciwnie są obliczane wyłącznie jako wartość parametru. Oprócz zabezpieczeń zapewnianych poleceń sparametryzowanych zapewniają wygodną metodę służący do organizowania wartości przekazane za pomocą instrukcji języka Transact-SQL lub procedury składowanej.  
  
 Aby uzyskać więcej informacji na temat korzystania z poleceń sparametryzowanych zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Parametry elementu DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Opisuje sposób używania parametrów za pomocą `DataAdapter`.|  
|[Modyfikowanie danych za pomocą procedur składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|W tym artykule opisano, jak określić parametry i uzyskać wartość zwracaną.|  
|[Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|W tym artykule opisano, jak hermetyzują dostęp do danych za pomocą procedur składowanych serwera SQL Server.|  
  
## <a name="script-exploits"></a>Luki w zabezpieczeniach skryptu  
 Wykorzystanie skryptu jest inna forma iniekcji używającej złośliwego znaków wstawione do strony sieci Web. Przeglądarka nie można zweryfikować wstawione znaki i będzie przetwarzać je jako część strony.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Przegląd luki w zabezpieczeniach skryptu](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|W tym artykule opisano sposób zabezpieczyć się przed skryptów i instrukcji SQL luki w zabezpieczeniach.|  
  
## <a name="probing-attacks"></a>Badanie ataków  
 Osoby atakujące często używają informacji z wyjątku, takie jak nazwa serwera, bazy danych lub tabeli, aby zainstalować ataku w systemie. Ponieważ wyjątki mogą zawierać określone informacje na temat aplikacji lub źródła danych, można zabezpieczyć ze źródłem danych i aplikacji lepiej chroniony przez tylko udostępnianie istotnych informacji klientowi.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podstawowe założenia obsługi wyjątków](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|W tym artykule opisano podstawowe rodzaje try/catch/finally strukturalna Obsługa wyjątków.|  
|[Najlepsze rozwiązania dotyczące wyjątków](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|W tym artykule opisano najlepsze rozwiązania dotyczące obsługi wyjątków.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Ochrona programu Microsoft Access i źródła danych programu Excel  
 Program Microsoft Access i Microsoft Excel może działać jako magazyn danych na potrzeby aplikacji ADO.NET, gdy wymagania dotyczące zabezpieczeń są minimalne lub nie istnieje. Ich funkcje bezpieczeństwa, zostaną zastosowane na przed intruzami, ale nie należy polegać na więcej niż zniechęcić meddling przez użytkowników w organizacji uninformed. Pliki danych fizycznych dostępu i programu Excel istnieje w systemie plików, a musi być dostępna dla wszystkich użytkowników. To sprawia, że ich narażone na ataki, mogącymi skutkować kradzieżą lub utraty danych, ponieważ pliki można łatwo skopiować lub zmodyfikować. Gdy wymagana jest niezawodne zabezpieczenia, użyj programu SQL Server lub innej bazy danych, które są oparte na serwerze plików danych fizycznych których nie można odczytać z systemu plików.  
  
 Aby uzyskać więcej informacji na temat ochrony danych programu Access i program Excel zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zagadnienia dotyczące zabezpieczeń i wskazówki dotyczące programu Access 2007](https://go.microsoft.com/fwlink/?LinkId=98354)|W tym artykule opisano technik zabezpieczeń dla programu Access 2007 takich szyfrowania plików, administrowanie hasła, Konwersja bazy danych do nowego formatu ACCDB i ACCDE i przy użyciu innych opcji zabezpieczeń.|  
|[Ochrona bazy danych programu Access z poziomu użytkownika zabezpieczeń (MDB)](https://go.microsoft.com/fwlink/?LinkId=47697)|Dotyczy 2003 dostępu. Instrukcje dotyczące implementowania zabezpieczeń na poziomie użytkownika w celu ochrony danych w programie Access 2003.|  
|[Opis roli pliki informacji o grupie roboczej w zabezpieczenia dostępu](https://support.microsoft.com/kb/305542)|Wyjaśniono, roli i relacji tego pliku w usłudze security 2003 dostępu.|  
|[Często zadawane pytania dotyczące zabezpieczeń firmy Microsoft dostęp dla programu Microsoft Access w wersji 2.0 za pomocą 2000](https://go.microsoft.com/fwlink/?LinkId=47698)|Wersja do pobrania dostępu firmy Microsoft Security — często zadawane pytania.|  
|[Rozwiązywanie problemów dotyczących zabezpieczeń i ochrony](https://go.microsoft.com/fwlink/?LinkId=47703)|Przedstawia rozwiązania typowych problemów z zabezpieczeniami w programie Excel 2003.|  
  
## <a name="enterprise-services"></a>Enterprise Services  
 COM + zawiera własny model zabezpieczeń, która opiera się na konta Windows NT i personifikacji wątku/procesu. <xref:System.EnterpriseServices> Przestrzeń nazw zapewnia otoki, które umożliwiają aplikacji platformy .NET do integracji aplikacji kod zarządzanego przy użyciu zabezpieczeń usług COM + za pośrednictwem <xref:System.EnterpriseServices.ServicedComponent> klasy.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[COM + opartej na rolach zabezpieczeń i .NET Framework](https://msdn.microsoft.com/library/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|W tym artykule omówiono sposób integracji aplikacji kod zarządzanego przy użyciu usług zabezpieczeń modelu COM +.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym  
 .NET Framework oferuje interakcji z niezarządzanego kodu, w tym modelu COM składników modelu COM + usług, zewnętrzne biblioteki typów i wielu usług systemu operacyjnego. Praca z kodem niezarządzanym obejmuje wydostawać obwodu zabezpieczeń dla kodu zarządzanego. Zarówno kod, jak i wszelki kod, który ją wywołuje musi mieć niezarządzanych uprawnień kodu (<xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określono flagę). Niezarządzanego kodu można wprowadzać luk w zabezpieczeniach niezamierzone do aplikacji. W związku z tym należy unikać współdziałanie z kodem niezarządzanym, chyba że jest to absolutnie konieczne.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)|Zawiera tematów opisujących sposób udostępnianie składników COM programowi .NET Framework oraz udostępnianie składników .NET Framework dla modelu COM.|  
|[Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)|Zawiera tematy zaawansowane, takie jak podstawowe zestawy międzyoperacyjne, wątków i przekazywanie niestandardowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Zalecenia dotyczące strategii dostępu do danych](https://msdn.microsoft.com/library/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
