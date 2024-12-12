simulation_time = 3600;
arrival_rate = 1/15;
service_rate = 1/20;
num_counters = 3;

time = 0;
queue = [];
counters = zeros(1, num_counters);
total_customers = 0;
served_customers = 0;
waiting_times = [];

while time < simulation_time
    inter_arrival_time = exprnd(1/arrival_rate);
    time = time + inter_arrival_time;

    if time > simulation_time
        break;
    end

    total_customers = total_customers + 1;
    queue = [queue, time];

    for i = 1:num_counters
        if counters(i) == 0 && ~isempty(queue)
            arrival_time = queue(1);
            queue(1) = [];
            service_time = exprnd(1/service_rate);
            counters(i) = service_time;
            waiting_time = time - arrival_time;
            waiting_times = [waiting_times, waiting_time];
            served_customers = served_customers + 1;
        end
    end

    counters = max(counters - inter_arrival_time, 0);
end

fprintf('Total customers arrived: %d\n', total_customers);
fprintf('Total customers served: %d\n', served_customers);
fprintf('Average waiting time: %.2f seconds\n', mean(waiting_times));
fprintf('Maximum waiting time: %.2f seconds\n', max(waiting_times));

figure;
histogram(waiting_times, 20);
title('Distribution of Waiting Times');
xlabel('Waiting Time (seconds)');
ylabel('Frequency');
grid on;
