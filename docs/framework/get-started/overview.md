---
title: Przegląd programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c844a81da036c5e96c2c619e3a3aae85f70f8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-the-net-framework"></a>Przegląd programu .NET Framework

.NET Framework jest technologia, która obsługuje tworzenie i uruchamianie nowej generacji aplikacji i usług XML sieci Web. .NET Framework zaprojektowano w celu spełnienia następujących celów:

- Aby zapewnić spójny zorientowane obiektowo środowiska programowania, czy kod obiektu są przechowywane i wykonywane lokalnie, wykonywane lokalnie, ale rozproszonych Internet lub zdalnie wykonać.

- Zapewnienie środowiska wykonywanie kodu, który minimalizuje konfliktów wdrożenia i przechowywanie wersji oprogramowania.

- Aby zapewnić środowisko wykonawcze kodu, które ułatwia bezpieczne wykonywanie kodu, w tym kod tworzony przez nieznaną lub częściowo zaufanych innych firm.

- Umożliwia wykonanie kodu środowiska, aby wyeliminować problemy z wydajnością z inicjowanych przez skrypty lub interpretowane środowisk.

- Aby można było spójne developer wystąpić powszechnie różnych typów aplikacji, takich jak aplikacje systemu Windows i aplikacji sieci Web.

- Aby utworzyć całej komunikacji na standardach, aby upewnić się, że kodu opartego na programie .NET Framework integruje się z innego kodu.

> [!NOTE]
> Aby uzyskać ogólne wprowadzenie do programu .NET Framework dla użytkowników i deweloperów, zobacz [wprowadzenie](../../../docs/framework/get-started/index.md).

.NET Framework zawiera środowisko uruchomieniowe języka wspólnego (CLR) i bibliotece klas programu .NET Framework. Środowisko uruchomieniowe języka wspólnego jest podstawą środowiska .NET Framework. Środowisko uruchomieniowe można traktować jako agenta, który zarządza kodu w czasie wykonywania, podając podstawowe usługi, takie jak zarządzanie pamięci, wątku i komunikacji zdalnej, również wymuszając ścisłe zasady zabezpieczeń i inne formy dokładności kodu, które podwyższyć poziom bezpieczeństwa i niezawodności. W rzeczywistości pojęcie zarządzania kodem jest podstawą środowiska uruchomieniowego. Kod, że elementy docelowe środowisko uruchomieniowe nosi nazwę kodu zarządzanego podczas kod, który nie docelowe środowisko uruchomieniowe nosi nazwę kodu niezarządzanego. Biblioteka klas jest kompleksowe, zorientowany obiektowo kolekcją typów wielokrotnego użytku, które umożliwia tworzenie aplikacji od tradycyjnych wiersza polecenia i graficzny interfejs użytkownika (GUI) aplikacje oparte na najnowszych rozwiązań dotyczących dostarczane przez platformę ASP.NET, takich jak Web apps Formularze oraz usługi XML sieci Web.

.NET Framework może być obsługiwany przez niezarządzane składników, które załadować środowisko uruchomieniowe języka wspólnego do ich procesów i zainicjować wykonywanie kodu zarządzanego, tworząc środowisko oprogramowania, który wykorzystuje funkcje zarządzane i niezarządzane. .NET Framework nie tylko udostępnia kilka hosty w czasie wykonywania, ale obsługuje również rozwoju hosty w czasie wykonywania innych firm.

Na przykład ASP.NET obsługuje środowisko wykonawcze zapewniające skalowalne, po stronie serwera środowisko dla kodu zarządzanego. Program ASP.NET działa bezpośrednio ze środowiskiem uruchomieniowym, aby umożliwić aplikacji ASP.NET i usługi XML sieci Web, które zostały omówione w dalszej części tego tematu.

Program Internet Explorer jest przykładem niezarządzanych aplikacji, która obsługuje środowisko uruchomieniowe (w formie rozszerzenia typu MIME). Przy użyciu programu Internet Explorer do obsługi środowiska uruchomieniowego umożliwia osadzanie składników zarządzanych lub formanty formularzy systemu Windows w dokumentach HTML. Hostowanie środowiska uruchomieniowego w ten sposób umożliwia przenośnych kodu zarządzanego, ale z lepsza oferuje tylko kodu zarządzanego, takich jak wykonanie częściowo zaufanych i pliku izolowanego magazynu.

Na poniższej ilustracji przedstawiono relacji środowiska CLR i biblioteki klas do aplikacji i całego systemu. Na rysunku przedstawiono również sposób zarządzany kod działa w większych architektury.

![Zarządzany kod w większych architektura](../../../docs/framework/get-started/media/circle.gif "koło") .NET Framework w kontekście

W poniższych sekcjach opisano główne funkcje programu .NET Framework większej liczby szczegółów.

## <a name="features-of-the-common-language-runtime"></a>Funkcje środowisko uruchomieniowe języka wspólnego

Środowisko uruchomieniowe języka wspólnego zarządza pamięci, wykonywanie wątków wykonywania kodu, weryfikowania bezpieczeństwa kodu, kompilacji i innych usługach system. Te funkcje są wewnętrzne do kodu zarządzanego, który jest uruchamiany na środowisko uruchomieniowe języka wspólnego.

Dotyczących zabezpieczeń zarządzane składniki są przyznawane różnych stopni zaufania, w zależności od szeregu czynników, które obejmują ich pochodzenia (np. Internet, sieci przedsiębiorstwa lub komputer lokalny). Oznacza to, że zarządzanego składnika może lub nie można wykonać operacji dostępu do plików, operacji dostępu do rejestru lub innych ważnych funkcji, nawet wtedy, gdy jest on używany w tej samej aktywnej aplikacji.

Środowisko uruchomieniowe wymusza także niezawodność kodu zaimplementowanie strict infrastruktury sprawdzania typu i kod wywołuje wspólny system typów (CTS). CTS zapewnia samoopisujące całego kodu zarządzanego. Różne firmy Microsoft i Kompilatory języka innych firm generowanie kodu zarządzanego, który odpowiada CTS. Oznacza to, że może on korzystać inne typy zarządzane i wystąpień, wymuszając ściśle typu wierności i typ bezpieczeństwa.

Ponadto zarządzanego środowiska wykonawczego eliminuje wiele typowych problemów z oprogramowaniem. Na przykład środowiska uruchomieniowego obsługuje układ obiektu i automatycznie zarządza odwołania do obiektów, zwalniając je, gdy są one już używane. To automatyczne zarządzanie pamięcią rozpoznaje dwie typowe błędy aplikacji, przecieki pamięci i błędne odwołania do pamięci.

Środowisko uruchomieniowe przyspiesza również produktywność deweloperów. Na przykład programistów pisać aplikacje w z wybranego języka programowania jeszcze w pełni korzystać z programu obsługi, biblioteki klas i składników napisanych w innych językach przez innych. Dowolnego dostawcy kompilatora, który chce docelowe środowisko uruchomieniowe można to zrobić. Kompilatory języka, które odnoszą się do programu .NET Framework udostępnia funkcje programu .NET Framework istniejący kod napisany w tym języku znacznie łatwiejszym proces migracji w przypadku istniejących aplikacji.

Gdy środowiska uruchomieniowego zaprojektowano pod kątem oprogramowania w przyszłości, obsługuje ona również oprogramowania dzisiaj i wczoraj. Współdziałanie zarządzane i niezarządzane kod umożliwia deweloperom nadal używać niezbędne składniki modelu COM i bibliotek DLL.

Środowisko wykonawcze ma na celu poprawę wydajności. Mimo że środowisko uruchomieniowe języka wspólnego udostępnia wiele standardowych usług czasu wykonania, nigdy nie jest interpretowany kodu zarządzanego. Funkcja o nazwie just in time (JIT) kompilowanie umożliwia zarządzanego kodu do uruchomienia w języku macierzystym maszyny systemu, na którym jest wykonywany. W tym samym czasie Menedżer pamięci usuwa możliwości fragmentacji pamięci i zwiększa pamięci miejscowości z — odwołanie do dalszego zwiększenia wydajności.

Na koniec środowisko uruchomieniowe może być obsługiwany przez aplikacje wysokiej wydajności, po stronie serwera, takie jak Microsoft SQL Server i usługi Internet Information Services (IIS). Ta infrastruktura umożliwia umożliwia zapisanie logiki biznesowej podczas nadal korzystających z wyższego poziomu wydajności branży najlepsze enterprise serwerów, które obsługuje środowisko uruchomieniowe hostingu kodu zarządzanego.

## <a name="net-framework-class-library"></a>Biblioteka klas programu .NET Framework

Biblioteka klas programu .NET Framework jest kolekcją typów wielokrotnego użytku, które ścisła integracja z środowisko uruchomieniowe języka wspólnego. Biblioteka klas jest obiektowej, zapewniając typów, z których kod zarządzany pochodzi funkcji. To nie tylko sprawia, że typy .NET Framework jest łatwy w użyciu, ale zmniejsza czas związany z poznanie nowych funkcji programu .NET Framework. Ponadto składników innych firm integrują się z klas w programie .NET Framework.

Na przykład klasy kolekcji .NET Framework implementuje zestaw interfejsów do tworzenia własnych klas kolekcji. W klasach kolekcji programu blend bezproblemowo z klas w programie .NET Framework.

Zgodnie z regułami z biblioteki klas zorientowane obiektowo, typy .NET Framework umożliwiają wykonywanie szeregu typowych zadań programowania, w tym zadań, takich jak zarządzanie ciągu, zbierania danych łączność z bazą danych i uzyskiwania dostępu do plików. Oprócz tych typowych zadań biblioteki klas zawiera typy, które obsługi różnych scenariuszy projektowych. Umożliwia tworzenie następujących typów aplikacji i usług .NET Framework:

- Aplikacje konsoli. Zobacz [Kompilowanie aplikacji konsoli](../../../docs/standard/building-console-apps.md).

- Graficzny interfejs użytkownika aplikacji (formularze systemu Windows) w systemie Windows. Zobacz [formularzy systemu Windows](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) aplikacji. Zobacz [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- Aplikacje programu ASP.NET. Zobacz [aplikacji ASP.NET sieci Web](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Usługi systemu Windows. Zobacz [wprowadzenie do systemu Windows usługi aplikacji](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Aplikacje zorientowane na usługę przy użyciu usługi Windows Communication Foundation (WCF). Zobacz [zorientowane na usługę aplikacje z usługą WCF](../../../docs/framework/wcf/index.md).

- Aplikacje z obsługą przepływu pracy przy użyciu systemu Windows Workflow Foundation (WF). Zobacz [tworzenia przepływów pracy w programie .NET Framework](http://msdn.microsoft.com/library/cbf3880f-dc7b-466d-b808-1109b1223f4a).

Klasy formularzy systemu Windows są rozbudowany zestaw typów wielokrotnego użytku, które znacząco upraszcza programowanie graficznego interfejsu użytkownika systemu Windows. Jeśli piszesz aplikację formularza sieci Web ASP.NET, można użyć klasy formularzy sieci Web.

## <a name="see-also"></a>Zobacz także

[Wymagania systemowe](../../../docs/framework/get-started/system-requirements.md)   
[Przewodnik instalacji](../../../docs/framework/install/index.md)   
[Podręcznik programowania](../../../docs/framework/development-guide.md)   
[Narzędzia](../../../docs/framework/tools/index.md)   
[.NET framework — przykłady](http://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)   
[Biblioteka klas programu .NET framework](http://go.microsoft.com/fwlink/?LinkID=227195)
