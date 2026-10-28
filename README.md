# Assignment-29-oct
Assignment on inheritance
#include <iostream>
using namespace std;

class BaseAccountClass {
public:
    virtual void SendMoney() {
        cout << "Permission denied: Account access restricted." << endl;
    }

    virtual void ReceiveMoney() {
        cout << "Permission denied: Account access restricted." << endl;
    }
};

class ConsumerAccountClass : public BaseAccountClass {
private:
    bool warning;

public:
    ConsumerAccountClass(bool warning) {
        this->warning = warning;
    }

    void SendMoney() override {
        if (warning == true)
            cout << "Send Money: Denied" << endl;
        else
            cout << "Send Money: Allowed" << endl;
    }

    void ReceiveMoney() override {
        if (warning == true)
            cout << "Receive Money: Denied" << endl;
        else
            cout << "Receive Money: Allowed" << endl;
    }
};

int main() {
    BaseAccountClass *account;

    ConsumerAccountClass userAccount(true);

    account = &userAccount;

    account->SendMoney();
    account->ReceiveMoney();

    return 0;
}
