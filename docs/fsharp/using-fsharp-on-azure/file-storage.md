---
title: 'Rozpoczynanie pracy z magazynem plików Azure przy użyciu języka F #'
description: Przechowywanie plików danych w chmurze za pomocą magazyn plików Azure i instalowanie udziału plików w chmurze z maszyny wirtualnej platformy Azure (VM) lub z lokalnych aplikacji systemu Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Rozpoczynanie pracy z magazynem plików Azure przy użyciu języka F # #

Magazyn plików Azure to usługa, która umożliwia udziałów plików w chmurze przy użyciu standardowego [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Obsługiwane są zarówno protokół SMB 2.1 i 3.0 protokołu SMB. Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania. Aplikacje działające na maszynach wirtualnych platformy Azure lub usługi w chmurze lub z klientami lokalnymi mogą zainstalować udział plików w chmurze, tak samo jak aplikacja na komputerze instalująca typowy udział SMB. Dowolna liczba składników aplikacji, a następnie można zainstalować i uzyskać jednocześnie dostęp do udziału plików magazynu.

Omówienie pojęć dotyczących magazynu plików, zobacz [przewodnik .NET do przechowywania plików](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).
Należy również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie skryptu języka F # i rozpocząć F # Interactive

Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #. Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `files.fsx`, w środowiska deweloperskiego F #.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `files.fsx` pliku:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobierz ciąg połączenia

Parametry połączenia magazynu Azure należy w tym samouczku. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników. Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Przy użyciu programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Tworzenie klienta usługi plików

`CloudFileClient` Typu umożliwia programowane używanie plików przechowywanych w magazynie plików. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu plików.

## <a name="create-a-file-share"></a>Tworzenie udziału plików

W tym przykładzie pokazano, jak utworzyć udział plików, jeśli jeszcze nie istnieje:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Utwórz katalog główny i podkatalogu

W tym miejscu możesz uzyskać katalogu głównego i uzyskać podkatalogiem katalogu głównego. Możesz utworzyć obie Jeśli jeszcze nie istnieje.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Przekaż tekst w formacie

Ten przykład przedstawia sposób przekazywania tekstu jako plik.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Pobierz plik do lokalnej kopii pliku

W tym miejscu Pobierz plik właśnie utworzony dołączania zawartości do pliku lokalnego.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Ustawianie maksymalnego rozmiaru udziału plików

W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału dla udziału. `FetchAttributes` musi zostać wywołana, aby wypełnić udziału `Properties`, i `SetProperties` propagowanie zmian lokalnych do usługi Magazyn plików Azure.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików

Możesz wygenerować sygnaturę dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku. Można również utworzyć zasady dostępu współdzielonego w udziale plików do zarządzania sygnaturami dostępu współdzielonego. Tworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie Sygnatur w przypadku powinien być naruszenia zabezpieczeń.

W tym miejscu Utwórz wspólne zasady w udziale dostępu, a następnie użyj tego zasad nakładane są ograniczenia na sygnatury dostępu Współdzielonego w pliku w udziale.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [za pomocą sygnatur dostępu do udostępnionych (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) i [tworzenie i używanie sygnatury dostępu Współdzielonego z magazynem obiektów Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Skopiuj pliki

Plik można skopiować do innego pliku, lub do obiektu blob oraz obiekty blob do pliku. Jeśli kopiujesz obiektu blob do pliku lub pliku do obiektu blob, możesz *musi* Użyj sygnatury dostępu współdzielonego (SAS) do uwierzytelniania obiektu źródłowego, nawet jeśli kopiujesz w ramach tego samego konta magazynu.

### <a name="copy-a-file-to-another-file"></a>Kopiowanie pliku do innego pliku

W tym miejscu można skopiować pliku do innego pliku w tym samym udziale. Ponieważ ta operacja kopiowania kopiuje między plikami w tym samym koncie magazynu, można użyć uwierzytelniania klucza wspólnego do wykonania kopii.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopiowanie pliku do obiektu blob

W tym miejscu Utwórz plik i skopiuj go do obiektu blob w ramach tego samego konta magazynu. Możesz utworzyć sygnatury dostępu Współdzielonego dla pliku źródłowego, który usługa używa do uwierzytelniania dostępu do pliku źródłowego podczas operacji kopiowania.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

W ten sam sposób można skopiować obiektu blob do pliku. Jeśli obiekt źródłowy jest obiektem blob, następnie utwórz sygnaturę dostępu Współdzielonego w celu uwierzytelniania dostępu do tego obiektu blob podczas operacji kopiowania.

## <a name="troubleshooting-file-storage-using-metrics"></a>Rozwiązywanie problemów z magazynem plików przy użyciu metryk

Analizy usługi Azure Storage obsługuje metryki dla usługi Magazyn plików. Dane metryk możesz Śledzenie żądań i diagnozowanie problemów.

Można włączyć metryki dla usługi Magazyn plików [Azure Portal](https://portal.azure.com), lub czy z F # następująco:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Następne kroki

Zobacz następujące łącza, aby uzyskać więcej informacji na temat usługi Magazyn plików Azure.

### <a name="conceptual-articles-and-videos"></a>Artykuły koncepcyjne i filmy

- [Azure File Storage: frictionless cloud SMB systemu plików dla systemu Windows i Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak używać magazynu plików Azure z systemem Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Narzędzia dostępne do przechowywania plików

- [Używanie programu Azure PowerShell z usługą Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Jak używać narzędzia AzCopy z usługi Magazyn Microsoft Azure](/azure/storage/storage-use-azcopy)
- [Przy użyciu interfejsu wiersza polecenia platformy Azure z usługą Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Tematy pomocy

- [Biblioteka klienta usługi Storage dla platformy .NET odwołania](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dokumentacja interfejsu API REST usługi plików](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Wpisy na blogu

- [Magazyn plików Azure jest ogólnie dostępna teraz](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Wprowadzenie do usługi Microsoft Azure pliku](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Utrwalanie połączeń pliki programu Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
