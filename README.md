# uikit_alert_in_swiftui

```swift
final class UIKitAlert {
    static func showCouponAlert(
        title: String = "Do you have an invitation code?".localized(),
        message: String = "Enter the invitation code\nto receive a 14-day free trial pass!".localized(),
        onOk: @escaping (String) -> Void,
        onCancel: @escaping () -> Void
    ) {
        let alert = UIAlertController(
            title: title,
            message: message,
            preferredStyle: .alert
        )
        alert.addTextField()
        alert.addAction(
            .init(
                title: "OK".localized(),
                style: .default,
                handler: { action in
                    guard let text = alert.textFields?.first?.text else { return }
                    onOk(text)
                }
            )
        )
        alert.addAction(
            .init(
                title: "Cancel".localized(),
                style: .cancel
            )
        )
        UIApplication.shared.topMostViewController?.present(alert, animated: true)
    }

}

```
