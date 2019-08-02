---
title: Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F#
description: Przechowuj dane plików w chmurze za pomocą usługi Azure File Storage i instaluj udział plików w chmurze z maszyny wirtualnej platformy Azure lub z aplikacji lokalnej z systemem Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a0e3cab56ba0f3db27335822616b4976a5d9de62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630496"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F\#

Azure File Storage to usługa, która oferuje udziały plików w chmurze przy użyciu standardowego [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Obsługiwane są wersje 2.1 i 3.0 protokołu SMB. W usłudze Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania. Aplikacje uruchomione na maszynach wirtualnych lub w ramach usług w chmurze platformy Azure, a także na klientach lokalnych mogą instalować udziały plików w chmurze tak samo jak aplikacja na komputerze instalująca typowy udział SMB. Dowolna liczba składników aplikacji może następnie równocześnie zainstalować udział Magazynu plików i uzyskiwać do niego dostęp.

Aby zapoznać się z omówieniem koncepcyjnym usługi File Storage, zobacz [Przewodnik po platformie .NET dotyczący usługi File Storage](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account).
Wymagany jest również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz F# skrypt i uruchom F# interaktywny

Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie. Aby utworzyć F# skrypt, Utwórz plik z `.fsx` rozszerzeniem, na przykład `files.fsx`w środowisku F# deweloperskim.

Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [](https://www.nuget.org/) `WindowsAzure.Storage` NuGet, aby zainstalować `#r` pakiet i odwołanie `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `files.fsx` pliku:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobierz parametry połączenia

W tym samouczku będą potrzebne parametry połączenia usługi Azure Storage. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).

Na potrzeby samouczka wprowadzisz w skrypcie parametry połączenia, takie jak:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu. Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu. Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych. Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.

W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Korzystanie z usługi Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak `ConfigurationManager` typ .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, użyj:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Spowoduje to zwrócenie elementu `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Tworzenie klienta usługi plików

`CloudFileClient` Typ pozwala programistycznie używać plików przechowywanych w magazynie plików. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z magazynu plików i zapisuje je w nim.

## <a name="create-a-file-share"></a>Tworzenie udziału plików

Ten przykład pokazuje, jak utworzyć udział plików, jeśli jeszcze nie istnieje:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Tworzenie katalogu głównego i podkatalogu

W tym miejscu otrzymujesz katalog główny i uzyskasz podkatalog w katalogu głównym. Należy utworzyć obie, jeśli jeszcze nie istnieją.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Przekaż tekst jako plik

Ten przykład pokazuje, jak przekazać tekst jako plik.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Pobierz plik do lokalnej kopii pliku

W tym miejscu pobierasz utworzony plik, dołączając zawartość do pliku lokalnego.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Ustaw maksymalny rozmiar udziału plików

W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału i jak ustawić limit przydziału dla udziału. `FetchAttributes`musi być wywołana `Properties`, aby wypełnić udział i `SetProperties` propagowanie lokalnych zmian do usługi Azure File Storage.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików

Można wygenerować sygnaturę dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku. Możesz również utworzyć zasady dostępu współdzielonego w udziale plików, aby zarządzać sygnaturami dostępu współdzielonego. Zaleca się utworzenie zasad dostępu współdzielonego, ponieważ zapewnia to możliwość odwoływania SAS, jeśli powinien zostać naruszony.

W tym miejscu można utworzyć zasady dostępu współdzielonego w udziale, a następnie użyć tych zasad w celu zapewnienia ograniczeń dla SAS dla pliku w udziale.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Aby uzyskać więcej informacji na temat tworzenia sygnatur dostępu współdzielonego i korzystania z nich, zobacz [Używanie sygnatur dostępu współdzielonego (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) i [Tworzenie i używanie SAS z magazynem obiektów BLOB](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopiuj pliki

Plik można skopiować do innego pliku lub do obiektu BLOB lub do pliku. Jeśli kopiujesz obiekt BLOB do pliku lub pliku do obiektu BLOB, *musisz* użyć sygnatury dostępu współdzielonego do uwierzytelnienia obiektu źródłowego, nawet jeśli kopiujesz w ramach tego samego konta magazynu.

### <a name="copy-a-file-to-another-file"></a>Kopiowanie pliku do innego pliku

W tym miejscu skopiujesz plik do innego pliku w tym samym udziale. Ponieważ ta operacja kopiowania Kopiuje między plikami na tym samym koncie magazynu, można użyć uwierzytelniania klucza współużytkowanego do wykonania kopii.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopiowanie pliku do obiektu BLOB

Tutaj utworzysz plik i skopiujesz go do obiektu BLOB w ramach tego samego konta magazynu. Tworzysz sygnaturę dostępu współdzielonego dla pliku źródłowego, którego usługa używa do uwierzytelniania w pliku źródłowym podczas operacji kopiowania.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Obiekt BLOB można skopiować do pliku w taki sam sposób. Jeśli obiekt źródłowy to obiekt BLOB, Utwórz sygnaturę dostępu współdzielonego, aby uwierzytelnić dostęp do tego obiektu BLOB podczas operacji kopiowania.

## <a name="troubleshooting-file-storage-using-metrics"></a>Rozwiązywanie problemów z magazynem plików przy użyciu metryk

Analityka magazynu platformy Azure obsługuje metryki dla usługi File Storage. Dane metryk umożliwiają śledzenie żądań i diagnozowanie problemów.

Metryki dla usługi File Storage można włączyć w [witrynie Azure Portal](https://portal.azure.com)lub można to zrobić w F# następujący sposób:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Następne kroki

Zobacz te linki, aby uzyskać więcej informacji na temat usługi Azure File Storage.

### <a name="conceptual-articles-and-videos"></a>Artykuły koncepcyjne i wideo

- [Azure Files Storage: system plików SMB w chmurze bezproblemowych dla systemów Windows i Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak korzystać z usługi Azure File Storage z systemem Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Narzędzia obsługujące magazyn plików

- [Używanie Azure PowerShell z usługą Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Jak używać AzCopy z Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Korzystanie z interfejsu wiersza polecenia platformy Azure z usługą Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Tematy pomocy

- [Dokumentacja biblioteki klienta usługi Storage dla platformy .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dokumentacja interfejsu API REST usługi plików](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Wpisy w blogu

- [Usługa Azure File Storage jest teraz ogólnie dostępna](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Wewnątrz File Storage platformy Azure](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Wprowadzenie do usługi plików Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Utrwalanie połączeń z plikami Microsoft Azure](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
