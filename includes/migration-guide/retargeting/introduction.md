## <a name="introduction"></a>Wprowadzenie
Zmiany retargetingu wpływa na aplikacje, które są ponownie kompilowana pod kątem różnych .NET Framework. Obejmują one:

* Zmiany w środowisku projektowania. Na przykład narzędzia kompilacji może emitować ostrzeżenia, jeśli wcześniej nie jak.

* Zmiany środowiska uruchomieniowego. Wpływają one na tylko te aplikacje, konkretnie ukierunkowane retargeted .NET Framework. Aplikacje, które odnoszą się do poprzednich wersji programu .NET Framework zachowują się tak samo, jak podczas uruchamiania w tych wersjach.

W tematach opisano zmiany retargetingu możemy zostały sklasyfikowane poszczególne elementy przez ich oczekiwanej wpływ w następujący sposób:

**Główne** to istotna zmiana, który ma wpływ na wiele aplikacji lub wymagają znacznej modyfikacji kodu.

**Drobne** jest to zmiana, który ma wpływ na małej liczby aplikacji lub wymagają drobne zmiany kodu.

**Krawędzi przypadku** jest to zmiana, która wpływa na aplikacje w bardzo konkretnych scenariuszy, które nie są typowe.

**Przezroczysty** to zmiany, która nie ma zauważalnego wpływu na deweloperem aplikacji lub użytkownika. Aplikacja nie powinny wymagać modyfikacji z powodu tej zmiany.
