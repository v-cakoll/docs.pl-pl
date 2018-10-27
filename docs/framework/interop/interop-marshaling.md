---
title: Marshaling międzyoperacyjny
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, COM interop
- interop marshaling
- interop marshaling, about interop marshaling
ms.assetid: 115f7a2f-d422-4605-ab36-13a8dd28142a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a70548231454991060098908ce954bf699eff838
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453258"
---
# <a name="interop-marshaling"></a>Marshaling międzyoperacyjny
<a name="top"></a> Marshaling międzyoperacyjny decyduje o tym, jak dane są przekazywane w metodzie argumentów i zwracanych wartości między zarządzanymi i niezarządzanymi pamięci podczas wywołania. Marshaling międzyoperacyjny jest czynnością środowiska wykonawczego, wykonywane przez usługę organizowania wykonywalnych języka wspólnego.  
  
 Większość typów danych mają wspólne reprezentacji w pamięci zarządzanych i niezarządzanych. Organizator międzyoperacyjny obsługuje następujące typy dla Ciebie. Inne typy może być niejednoznaczne lub nie jest reprezentowana w ogóle w pamięci zarządzanej.  
  
 Niejednoznaczny typ może mieć wiele reprezentacji niezarządzanych, mapowane na jeden typ zarządzany, albo brakuje informacji o typie, takich jak rozmiar tablicy. Niejednoznacznych typów Organizator zawiera reprezentację domyślne i Reprezentacje alternatywne, w których istnieje wiele reprezentacji. Możesz podać jawne instrukcje można organizatora, w jaki jest do organizowania niejednoznaczny typ.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Wywołanie platformy i modele międzyoperacyjnego modelu COM](#platform_invoke_and_com_interop_models)  
  
-   [Marshaling i Apartamentach COM](#marshaling_and_com_apartments)  
  
-   [Kierowanie wywołań zdalnych](#marshaling_remote_calls)  
  
-   [Tematy pokrewne](#related_topics)  
  
-   [Dokumentacja](#reference)  
  
<a name="platform_invoke_and_com_interop_models"></a>   
## <a name="platform-invoke-and-com-interop-models"></a>Wywołanie platformy i modele międzyoperacyjnego modelu COM  
 Środowisko uruchomieniowe języka wspólnego zawiera dwa mechanizmy współdziałanie z kodem niezarządzanym:  
  
-   Wywołanie platformy, które umożliwia kodowi zarządzanemu wywoływania funkcji wyeksportowanych z biblioteką niezarządzaną.  
  
-   Usługa międzyoperacyjna modelu COM, który umożliwia interakcję z obiektami Component Object Model (COM) za pośrednictwem interfejsów kodu zarządzanego.  
  
 Wywołanie obie platformy i COM międzyoperacyjny Użyj marshaling międzyoperacyjny dokładnie przenoszenie argumenty metody między obiekt wywołujący i obiekt wywoływany i z powrotem, jeśli wymagane. Jak pokazano na poniższej ilustracji, wywołania platformy przepływy wywołanie metody z kodu zarządzanego do kodu niezarządzanego i nigdy nie inny sposób, chyba że [funkcji wywołania zwrotnego](callback-functions.md) są zaangażowani. Mimo że wywołanie platformy wywołania mogą przepływać tylko z kodu zarządzanego do kodu niezarządzanego, dane mogą przepływać w obu kierunkach, jako parametry wejściowe i wyjściowe. Wywołań metod międzyoperacyjnego modelu COM może przepływać w obu kierunkach.  
  
 ![Wywołanie platformy](./media/interopmarshaling.png "interopmarshaling")  
Wywołanie platformy i przepływ wywołań międzyoperacyjnych COM  
  
 Na najniższym poziomie zarówno mechanizmów używać tego samego międzyoperacyjnego organizowanie usług. Jednak niektóre typy danych są obsługiwane wyłącznie przez COM interop lub wywołania platformy. Aby uzyskać więcej informacji, zobacz [domyślne zachowanie Marshalingu](default-marshaling-behavior.md).  
  
 [Powrót do początku](#top)  
  
<a name="marshaling_and_com_apartments"></a>   
## <a name="marshaling-and-com-apartments"></a>Marshaling i Apartamentach COM  
 Organizator międzyoperacyjny kieruje dane między stosie uruchomieniowym wspólnego języka i niezarządzanym stosu. Marshaling występuje zawsze, gdy obiektami wywołującym i wywoływanym nie może działać na tym samym wystąpieniu danych. Organizator międzyoperacyjny umożliwia obiektami wywołującym i wywoływanym były widoczne dla działających na tych samych danych, nawet jeśli mają własne kopię danych.  
  
 COM ma również organizatora, który kieruje dane między apartamentach COM lub różnych procesów COM. Przy wywoływaniu między kodem zarządzanym i niezarządzanym w obrębie tego samego apartamentu COM, organizator międzyoperacyjny jest tylko organizatora zaangażowane. Przy wywoływaniu między kodem zarządzanym i kodu niezarządzanego w różnych apartamentu COM lub innego procesu, organizator międzyoperacyjny i Organizator modelu COM są zaangażowane.  
  
### <a name="com-clients-and-managed-servers"></a>Klienci COM i serwerów zarządzanych  
 Wyeksportowane serwera zarządzanego z biblioteki typów są rejestrowane przez [Regasm.exe (narzędzie rejestracji zestawów)](../tools/regasm-exe-assembly-registration-tool.md) ma `ThreadingModel` wpis rejestru równa `Both`. Ta wartość wskazuje, że serwer można aktywować apartamentem jednowątkowym (przedziale STA) lub wielowątkowe apartamentu (MTA). Obiekt serwera jest tworzony w tej samej apartamentu jako obiektu wywołującego, jak pokazano w poniższej tabeli.  
  
|Klient modelu COM|Serwer .NET|Charakteryzuje się wymaganiami|  
|----------------|-----------------|-----------------------------|  
|STA|`Both` staje się komórce jednowątkowej|Marshaling tego samego typu apartment.|  
|MTA|`Both` staje się MTA.|Marshaling tego samego typu apartment.|  
  
 Ponieważ klient i serwer znajdują się w tej samej typu apartment, interop marshaling usługi automatycznie obsługuje marshaling wszystkich danych. Poniższa ilustracja przedstawia międzyoperacyjny usługi organizowania działające między zarządzanymi i niezarządzanymi stosów w ramach tego samego typu apartment styl modelu COM.  
  
 ![Marshaling międzyoperacyjny](./media/interopheap.gif "interopheap")  
Tego samego typu apartment organizowania procesu  
  
 Jeśli planujesz eksportu serwera zarządzanego, należy pamiętać, określa, czy klient modelu COM apartamentu serwera. Serwerów zarządzanych, wywoływany przez klient modelu COM, zainicjować w MTA musi zapewnić bezpieczeństwo wątkowe.  
  
### <a name="managed-clients-and-com-servers"></a>Zarządzanych klientów i serwerów COM  
 Ustawieniem domyślnym dla klientów zarządzanych apartamentach jest MTA; Typ aplikacji klient modelu .NET można jednak zmienić domyślne ustawienie. Na przykład [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] ustawienie typu apartment klienta jest komórce jednowątkowej Możesz użyć <xref:System.STAThreadAttribute?displayProperty=nameWithType>, <xref:System.MTAThreadAttribute?displayProperty=nameWithType>, <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> właściwości lub <xref:System.Web.UI.Page.AspCompatMode%2A?displayProperty=nameWithType> właściwość, aby sprawdzić i zmienić ustawienia typu apartment klient zarządzany.  
  
 Tworzenie składnika ustawienie koligacji wątku serwera COM. W poniższej tabeli przedstawiono kombinacje ustawień apartamentu dla klientów programu .NET i serwerów COM. Pokazuje również, wynikowy marshaling wymagania dotyczące kombinacje.  
  
|Klient modelu .NET|Serwer COM|Charakteryzuje się wymaganiami|  
|-----------------|----------------|-----------------------------|  
|MTA (ustawienie domyślne)|MTA<br /><br /> STA|Marshaling międzyoperacyjny.<br /><br /> Współdziałanie i organizowanie COM.|  
|STA|MTA<br /><br /> STA|Współdziałanie i organizowanie COM.<br /><br /> Marshaling międzyoperacyjny.|  
  
 Gdy klienta zarządzanego i niezarządzanego serwera są tego samego typu apartment, współdziałanie marshaling usługi obsługuje kierowanie wszystkich danych. Jednak jeśli klienta i serwera są inicjowane w apartamentach różnych, kierowanie modelu COM jest również wymagane. Na poniższej ilustracji pokazano elementy wywołania typu apartment krzyżowe.  
  
 ![COM marshaling](./media/singleprocessmultapt.gif "singleprocessmultapt")  
Wywołania między apartamentu między klient modelu .NET i obiektu COM  
  
 Dla typu apartment między organizowanie, należy wykonać następujące:  
  
-   Zaakceptuj obciążenie szeregowanie między apartamentu, który jest widoczne tylko wtedy, gdy istnieje wiele wywołań przez granicę. Należy zarejestrować biblioteki typów składnika modelu COM dla wywołań do pomyślnie przekroczenia granic typu apartment.  
  
-   Zmiany głównego wątku, ustawiając wątku klienta STA i MTA. Na przykład jeśli Twoja C# klient wywołuje wiele składników STA COM, możesz uniknąć apartamentu między organizowanie, ustawiając wątku głównego w komórce jednowątkowej  
  
    > [!NOTE]
    >  Gdy wątek C# klienta jest ustawiona na STA, wywołania składników MTA COM będzie wymagać między apartamentu marshaling.  
  
 Aby uzyskać instrukcje dotyczące jawne wybranie ustawienia modelu typu apartment, zobacz [zarządzane i niezarządzane wątkowości](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100)).  
  
 [Powrót do początku](#top)  
  
<a name="marshaling_remote_calls"></a>   
## <a name="marshaling-remote-calls"></a>Kierowanie wywołań zdalnych  
 Podobnie jak w przypadku wielu apartamentu organizowanie, kierowanie modelu COM jest zaangażowana w każdym wywołaniu między kodem zarządzanym i niezarządzanym zawsze wtedy, gdy obiekty znajdują się w osobnych procesach. Na przykład:  
  
-   Klient modelu COM, który wywołuje serwerów zarządzanych na zdalnym hoście używa rozproszonych (DCOM).  
  
-   Klient zarządzany, który wywołuje serwer COM, na zdalnym hoście używa protokołu DCOM.  
  
 Na poniższej ilustracji przedstawiono marshaling międzyoperacyjny jak i kierowanie modelu COM zapewniają kanałów komunikacyjnych granice procesu i hosta.  
  
 ![COM marshaling](./media/interophost.gif "interophost")  
Szeregowanie między procesami  
  
### <a name="preserving-identity"></a>Zachowywanie tożsamości  
 Środowisko uruchomieniowe języka wspólnego zachowuje tożsamość odwołania zarządzane i niezarządzane. Poniższa ilustracja przedstawia przepływ bezpośrednimi odwołaniami niezarządzane (górny wiersz) i bezpośredniego zarządzanych odwołania (dolny wiersz) granice procesu i hosta.  
  
 ![Wywoływana otoka COM i wywoływana otoka środowiska uruchomieniowego](./media/interopdirectref.gif "interopdirectref")  
Dokumentacja przechodzi przez granice procesu i hosta  
  
 Na tej ilustracji:  
  
-   Niezarządzany klient pobiera odwołanie do obiektu COM z obiektu zarządzanego, która pobiera odwołanie z hosta zdalnego. Mechanizm komunikacji zdalnej jest model DCOM.  
  
-   Klient zarządzany pobiera odwołanie do zarządzanego obiektu z obiektu COM, który pobiera odwołanie z hosta zdalnego. Mechanizm komunikacji zdalnej jest model DCOM.  
  
    > [!NOTE]
    >  Musi być zarejestrowana wyeksportowanej biblioteki typów z serwerów zarządzanych.  
  
 Liczba procesów granic między obiektami wywołującym i wywoływanym nie ma znaczenia; Ten sam bezpośredniego odwołuje się do występuje wywołań w procesie i spoza procesu.  
  
### <a name="managed-remoting"></a>Zarządzanych usług zdalnych  
 Środowisko wykonawcze zapewnia również zarządzanych usług zdalnych, używane do ustanawiania kanału komunikacyjnego między obiektami zarządzanej granice procesu i hosta. Zarządzane komunikacji zdalnej może obsłużyć zapory między składnikami komunikujące się, jak pokazano na następującym rysunku.  
  
 ![Protokół SOAP lub TcpChannel](./media/interopremotesoap.gif "interopremotesoap")  
Zdalne wywołania przez zapory za pomocą protokołu SOAP lub klasy TcpChannel  
  
 Niektóre wywołania niezarządzanych może channeled za pośrednictwem protokołu SOAP, takie jak wywołania między obsługiwanych składników i modelu COM.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Domyślne zachowanie marshalingu](default-marshaling-behavior.md)|W tym artykule opisano reguły, które międzyoperacyjny usługa kierowania używa do organizowania danych.|  
|[Marshaling danych w wywołaniu platformy](marshaling-data-with-platform-invoke.md)|W tym artykule opisano, jak deklarować parametrów metod i przekazywać argumenty do funkcji eksportowanych przez niezarządzanych bibliotek.|  
|[Marshaling danych za pomocą modelu COM](marshaling-data-with-com-interop.md)|Opisuje sposób dostosowywania otoki COM, aby zmienić zachowanie organizowania.|  
|[Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)|W tym artykule opisano, jak przeprowadzić migrację z modelu DCOM do WCF.|  
|[Instrukcje: Mapowanie wyników HRESULT i wyjątków](how-to-map-hresults-and-exceptions.md)|W tym artykule opisano sposób mapowania niestandardowej wyjątków na wartości HRESULT i zapewnia pełną mapowania od każdego HRESULT do jej klasy porównywalne wyjątków w programie .NET Framework.|  
|[Międzyoperacyjne używanie typów ogólnych](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100))|W tym artykule opisano akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.|  
|[Współdziałanie z kodem niezarządzanym](index.md)|Opisuje współdziałanie usługi udostępniane przez środowisko uruchomieniowe języka wspólnego.|  
|[Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Zawiera łącza do dodatkowych informacji o dołączaniu składników COM do aplikacji środowiska .NET Framework.|  
|[Zagadnienia dotyczące projektowania do celów międzyoperacyjności](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))|Zawiera wskazówki dotyczące pisania zintegrowane składników COM.|  
  
 [Powrót do początku](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Runtime.InteropServices?displayProperty=nameWithType>  
  
 [Powrót do początku](#top)
