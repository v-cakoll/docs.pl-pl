---
title: 'Porady: tworzenie otok COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4deb355a7b523437ae31a1d2b9c79e3b8d4f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-com-wrappers"></a>Porady: tworzenie otok COM
Otoki składnika modelu COM (Object) można tworzyć przy użyciu [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] funkcji lub .NET Framework Tlbimp.exe i Regasm.exe narzędzi. Obie metody generowania otoki COM dwa typy:  
  
-   A [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) z biblioteki typów do uruchamiania obiektów COM w kodzie zarządzanym.  
  
-   A [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) przy użyciu ustawień wymaganych do uruchomienia zarządzanego obiektu w natywnej aplikacji.  
  
 W [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można dodać otoki COM jako odwołanie do projektu.  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a>Zawijanie obiektów COM w zarządzanej aplikacji  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Aby utworzyć wywoływana otoka środowiska uruchomieniowego za pomocą programu Visual Studio  
  
1.  Otwórz projekt aplikacji zarządzanej.  
  
2.  Na **projektu** menu, kliknij przycisk **Pokaż wszystkie pliki**.  
  
3.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
4.  W oknie dialogowym Dodawanie odwołania, kliknij przycisk **COM** , a następnie wybierz składnik, należy użyć, a następnie kliknij przycisk **OK**.  
  
     W **Eksploratora rozwiązań**, należy pamiętać, że składnik modelu COM został dodany do folderu odwołań w projekcie.  
  
 Teraz można napisać kod, aby uzyskać dostęp do obiektu COM. Możesz rozpocząć od zadeklarowania obiektów, takich jak z `Imports` instrukcji dla [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] lub `Using` instrukcji dla [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].  
  
> [!NOTE]
>  Jeśli chcesz składniki programu Microsoft Office, najpierw zainstaluj [podstawowe zestawy międzyoperacyjne pakietu Office Microsoft](http://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) z Microsoft Download Center. W kroku 4, wybierz najnowszą wersję biblioteki dostępne dla produktów Office ma, takich jak **Microsoft Word 11.0 biblioteki**.  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć wywoływana otoka środowiska uruchomieniowego za pomocą narzędzi .NET Framework  
  
-   Uruchom [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) narzędzia.  
  
 To narzędzie tworzy zestawu zawierającego metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnym biblioteki typów.  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a>Zawijanie zarządzanych obiektów w aplikacji natywnej  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Aby utworzyć wywoływana otoka COM za pomocą programu Visual Studio  
  
1.  Tworzenie projektu biblioteki klas zarządzanych klasy, która ma zostać uruchomione w kodzie natywnym. Klasa musi mieć konstruktora domyślnego.  
  
     Sprawdź, czy Zakończenie Czteroczęściowy numer wersji dla programu zestawu w pliku AssemblyInfo. Ta liczba jest wymagana do obsługi przechowywania wersji w rejestrze systemu Windows. Aby uzyskać więcej informacji o numerach wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
3.  Kliknij przycisk **skompilować** kartę.  
  
4.  Wybierz **Zarejestruj dla międzyoperacyjności z modelem COM** pole wyboru.  
  
 Podczas kompilowania projektu zestawu jest automatycznie rejestrowana COM interop. Jeśli tworzysz natywnych aplikacji [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], można użyć zestawu, klikając **Dodaj odwołanie** na **projektu** menu.  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Aby utworzyć wywoływana otoka COM za pomocą narzędzi .NET Framework  
  
-   Uruchom [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) narzędzia.  
  
 To narzędzie umożliwia odczytanie metadanych zestawu i dodaje niezbędne wpisy do rejestru. W związku z tym klienci COM tworzyć .NET Framework klasy przezroczysty. Tak, jakby była natywnego klasy COM, można użyć zestawu.  
  
 Uruchom Regasm.exe w zestawie znajduje się w dowolnym katalogu, a następnie uruchom [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) Aby przenieść ją do globalnej pamięci podręcznej zestawów. Przenoszenie zestawu unieważnia wpisy rejestru lokalizacji, ponieważ w pamięci podręcznej GAC są zawsze przeanalizować, jeśli zestaw nie znajduje się w innym miejscu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [Wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md)
